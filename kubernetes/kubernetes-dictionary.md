# Kubernetes Dictionary

## Kubernetes

* 컨테이너 `오케스트레이션` 도구
* 여러 대의 도커 스웜 모드처럼 여러 대의 도커 호스트를 하나의 클러스터로 만들어 주는 점은 같지만, 세부적인 기능을 더욱 폭넓게 제공하고 있다. 때문에 실제 서비스 운영 단계에서 쿠버네티스가 가장 많이 쓰이고 있다.
* 서버 자원 클러스터링, 마이크로서비스 구조의 컨테이너 배포, 서비스 장애 복구 등 컨테이너 기반의 서비스 운영에 필요한 대부분의 오케스트레이션 기능을 지원.
* 영속적 볼륨, 스케쥴링, 장애 복구, 오토 스케일링, 서비스 디스커버리 및 인그레스 등 컨테이너 기반의 클라우드를 운영할 때 필요한 대부분의 기능과 컴포넌트를 사용자가 직접 커스터마이징 할 수 있다.

## 개념

### Object

* 쿠버네티스는 대부분의 리소스를 '오브젝트' 라고 불리는 형태로 관리한다. 
* 도커 `스웜 모드`의 컨테이너의 묶음을 표현하기 위해 `서비스` 라는 것이 있는데, 컨테이너 리소스의 집합을 정의하긴 것이기 때문에 이것 또한 일종의 오브젝트라고 할 수 있다.
* 쿠버네티스에서 컨테이너의 집합(`pods`), 컨테이너의 집합을 관리하는 컨트롤러(`replica set`), 사용자(`service account`), 노드(`node`)까지도 하나의 오브젝트로 사용할 수 있다.

### master node (마스터 노드)

* 쿠버네티스는 여러 개의 컴포넌트로 구성돼 있다.
* 쿠버네티스 노드의 역할은 크게 `마스터`와 `워커`로 나뉘어 있다.
* 마스터 노드는 쿠버네티스가 제대로 동작할 수 있게 `클러스터`를 관리하는 역할을 담당한다.
* 마스터 노드에서는 `API 서버(kube-apiserver)`, `컨트롤러 매니저(kube-controller-manager)`, `스케줄러(kube-scheduler)`, `DNS 서버(coreDNS)` 등이 실행 된다.
* 모든 노드에서 오버레이 네트워크 구성을 위해 `프락시(kube-proxy)`와 `네트워크 플러그인(calico, flannel, etc)`이 실행 된다.
* 이러한 컴포넌트들은 기본적으로 도커 컨테이너로서 실행되고 있다. 마스터 노트에 `SSH`로 접속해 `docker ps` 명령어를 실행해 보면 많은 컨테이너가 실행되고 있는 것을 볼 수 있다.
* 쿠버네티스 클러스터 구성을 위해 ` kubelet`이라는 에이전트가 모든 노드에서 실행된다.

### worker node (워커 노드)

* 쿠버네티스는 여러 개의 컴포넌트로 구성돼 있다.
* 쿠버네티스 노드의 역할은 크게 `마스터`와 `워커`로 나뉘어 있다.
* 워커 노드에는 애플리케이션 `컨테이너`가 생성된다
* 모든 노드에서 오버레이 네트워크 구성을 위해 `프락시(kube-proxy)`와 `네트워크 플러그인(calico, flannel, etc)`이 실행 된다.
* 이러한 컴포넌트들은 기본적으로 도커 컨테이너로서 실행되고 있다. 마스터 노트에 `SSH`로 접속해 `docker ps` 명령어를 실행해 보면 많은 컨테이너가 실행되고 있는 것을 볼 수 있다.
* 쿠버네티스 클러스터 구성을 위해 ` kubelet`이라는 에이전트가 모든 노드에서 실행된다.

### kubelet

* 쿠버네티스 클러스터 구성을 위한 에이전트
* 컨테이너의 생성, 삭제와 더불어 `마스터`와 `워커` 노드 간의 통신 역할을 함꼐 담당하는 매우 중요한 에이전트이다.
* kubelet이 정상적으로 실행되지 않은면 해당 노드는 쿠버네티스와 제대로 연결되지 않을 수도 있다.

### daemon (데몬)

* 유저가 직접 interact하는 프로그램이기 보다는 백그라운드 프로세스로 실행되는 컴퓨터 프로그램
* 쿠버네티스의 입장에서 보면 도커 데몬 또한 하나의 컴포넌트이다.
* The term was coined by the programmers at MIT's Project MAC. They took the name from Maxwell's demon, an imaginary being from a thought experiment that constantly works in the background, sorting molecules.

### Pod (포드)

* 컨테이너 애플리케이션을 배포하기 위한 기본 단위
* 1개 이상의 컨테이너로 구성된 컨테이너의 집합
* `도커 엔진`에서 기본 단위가 `도커 컨테이너`이고, `스웜 모드`에서 기본 단위가 여러 개의 컨테이너로 구성된 `서비스`인 것과 비슷한 맥락.
* 1개의 포드에는 1개의 컨테이너가 존재할 수도 있고, 여러 개의 컨테이너가 존재할 수도 있다.
* `Nginx` 웹 서비스를 쿠버네티스에서 생성하려면 포드 1개에 `Nginx` 컨테이너 1개만을 포함해 생성할 수 있다. 동일한 `Nginx` 컨테이너를 여러 개 생성하고 싶다면 1개의 `Nginx` 컨테이너가 들어 있는 동일한 포들르 여러 개 생성하면 된다.

### Nginx

* `reverse proxy`, `load balancer`, `mail proxy`, 그리고 `HTTP cache`로도 사용할 수 있는 웹 서버
* `로드밸런서`로 자주 사용되는  웹 서버.

### YAML

* 쿠버네티스는 명령어로도 사용할 수 있지만, YAML 파일을 더 많이 사용한다.
* 컨테이너뿐만 아니라 거의 모든 리소스 오브젝트들에 사용될 수 있다.
* 컨테이너의 설정값(ConfigMap), 비밀값(Secret) 등 모두 YAML 파일로 정의해 사용한다.
* 쿠버네티스에서 실제로 서비스를 배포할 때에도 `kubectl` 명령어가 아닌 여러개의 YAML 파일을 정의해 쿠버네티스에 적용시키는 방식으로 동작한다.
* 쿠버네티스를 잘 사용하는 방법을 한마디로 표현하여 'YAML 파일을 잘 작성하는 것'이라 하여도 과언이 아닐 정도로 중요하다.
* 쿠버네티스의 YAML 파일은 일반적으로 `apiVersion`, `kind`, `metadata`, `spec` 네 가지 항목으로 구성된다.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-nginx-pod
spec:
  containers:
  - name: my-nginx-container
    image: nginx:latest
    ports:
    - containerPort: 80
      protocol: TCP
```

### apiVersion

* `YAML` 파일에서 정의한 오브젝트의 API 버전을 나타낸다.
* 오브젝트의 종류 및 개발 성숙도에 따라 apiVersion의 설정 값이 달라질 수 있다.

### kind

* `YAML` 파일에서 리소스의 종류를 나타낸다.
* kind 항목에서 사용할 수 있는 리소스 오브젝트 종류는 `kubectl api-resources` 명령어의 KIND 항목에서 확인할 수 있다.

### metadata

* `YAML` 파일에서 라벨, 주석(annotation), 이름 등과 같은 리소스의 부가 정보들을 나타낸다.

### spec

* `YAML` 파일에서 리소스를 생성하기 위한 자세한 정보를 나타낸다.
* 예를 들어, 컨테이너 정보를 정의하는 `containers` 항목을 작성하고, 하위 항목인 `image`에서 사용할 도커 이미지를 지정할 수 있다. `name` 항목에서는 컨테이너의 이름을, `ports` 항목에서는 해당 컨테이너가 사용할 포드를 지정할 수 있다.


## 명령어

### kubectl api-resources

* 이 명령어를 통해 쿠버네티스에서 사용할 수 있는 오브젝트에는 어떤 것이 있는지 확인할 수 있다.

### kubectl explain <object name>

* 이 명령어를 통해 특정 오브젝트의 간단한 설명을 볼 수 있다
* 예시: `kubectl explain pods`

### kubectl apply -f <name_of_file.yaml>

* 작성한 `YAML` 파일은 해당 명령어로 쿠버네티스에 생성할 수 있다.
* 예를 들어 `포드`에 관한 설정이 담겨있는 파일 `nginx-pod.yaml`가 있다면, 다음 명령어 `kubectl apply -f nginx-pod.yaml`를 통해 새로운 포드를 생성할 수 있다.

### kubectl get <object name>

* 특정 오브젝트의 목록을 확인할 수 있다.
* 예를 들어 `kubectl get pods` 명령어는 현재 쿠버네티스에 존재하는 포드의 목록을 출력한다.

### kubectl describe <resource type> <resource name>

* 생성된 리소스의 자세한 정보를 얻어올 수 있다.
* 예를 들면, `kubectl describe pods my-nginx-pod`

### kubectl exec

* `docker exec` 명령어와 비슷하게 쿠버네티스에서도 이 명령어롤 통해 `포드`의 컨테이너에 명령어를 전달할 수 있다.
* `kubectl exec -it my-nginx-pod bash` 이 명령어를 통해 포드 컨테이너 내부로 들어가 배시 셸을 실행한다.

### kubectl logs <resource-name>

* 도커에서의 `docker logs`와 같이 쿠버네티스에서도 해당 명령어로 특정 리소스의 로그를 확인할 수 있다.
* 예를 들어 포드의 로그를 확인하고 싶다면 `kubectl logs my-nginx-pod`와 같이 사용하면 된다.

### kubectl delete -f <object_file.yaml>

* 쿠버네티스의 오브젝트를 삭제할 수 있는 명령어.
* 예를 들어 `nginx-pod.yaml`에 정의된 Nginx 포드를 삭제할 때 `kubectl delete -f nginx-pod.yaml`와 같이 명령어를 사용한다.
* 포드를 삭제할 때 위의 명령어 대신 `kubectl delete pod <pod name>`를 사용할 수 있다.
