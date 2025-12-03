## 테스트

1. yaml 파일 작성
2. yaml 파일 cluster에 적용 
   ```
    kubectl apply -f pvc.yaml
    kubectl apply -f pod.yaml
    kubectl apply -f service.yaml
   ```
3. pod 생성 결과 확인
    ```
    kubectl get pods
    ```

4. 자원 할당 결과 확인
    ```
    kubectl get pvc
    kubectl get pv
    ```

5. service 통한 애플리케이션에 post 요청 전송, 메시지 작성
    ```
        kubectl run curl --image=curlimages/curl -it --rm --restart=Never \
    --command -- curl -X POST -H "Content-Type: application/json" \
    -d '{"message":"hello from dynamic sc"}' http://sc-service:3000
    ```

6. service 통한 애플리케이션에 get 요청 전송, 메시지 읽기
    ```
    kubectl run curl --image=curlimages/curl -it --rm --restart=Never \
  --command -- curl http://sc-service:3000
    ```

7. Pod 삭제
    ```
    kubectl delete pod sc-demo
    ```

8. Pod 재생성
    ```
    kubectl apply -f pod.yaml
    ```

10. 임시 pod 만들어서 메시지 읽기 (Pod 삭제에도 유지됨)
    ```
    kubectl run curl --image=curlimages/curl -it --rm --restart=Never \ 
    --command -- curl http://sc-service:3000
    ```

## 결과

<img width="1326" height="447" alt="스크린샷 2025-12-03 오후 7 09 20" src="https://github.com/user-attachments/assets/8120f867-4210-49da-9dd6-fe36440e4398" />