## How to check if a server is running on a port and kill its process.

Date: 20190903

1. `lsof -i<portNumber>`
  
- Ex) To check if mongoDB is running on its default port: `lsof -i :27017`
  
2. `kill -9 <PID>` (PID: process ID)

   - Ex) `kill -9 27531`

   

