Troubleshooting CITSmart

1. Verificar containers
docker ps

2. Verificar consumo
docker stats --no-stream runITSM

3. Procurar OutOfMemory
docker logs runITSM 2>&1 | grep -i OutOfMemory

4. Identificar PID Java
docker exec -it runITSM ps -ef | grep java

5. Verificar heap
docker exec -it runITSM jcmd <PID> GC.heap_info

6. Baixar server.log pela interface administrativa

7. Verificar trilha de auditoria no horário da falha