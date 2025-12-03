## 테스트
1. 파일 작성

2. 클러스터에 저장소 선언

   ```kubectl apply -f pv.yaml```

3. Pod이 사용할 저장소 요청

    ```kubectl apply -f pvc.yaml```

4. Pod 생성, express 앱 구동, PVC 마운트

   ```kubectl apply -f pod.yaml```

5. 내부 접속 위한 ClusterIP 서비스 설정

   ```kubectl apply -f service.yaml```

6. Pod 생성 및 구동 확인

   ```kubectl get pods```

7. 파일에 메시지 저장

   ```
   kubectl run curl --image=curlimages/curl -it --rm --restart=Never -- \
   curl -X POST -H "Content-Type: application/json" \
   -d '{"message":"hello from pvc"}' http://pv-service:3000 
  ```

8. 파일 메시지 읽기

   ```
   kubectl run curl --image=curlimages/curl -it --rm --restart=Never \ 
   --command -- curl http://pv-service:3000
   ```

9. Pod 삭제
 
   ``` kubectl delete pod pv-demo```

10. Pod 재생성 
11. 파일 메시지 다시 읽기 

## 결과 확인
