# 도커(Docker) 사용법

## 이미지 관리
```bash
docker images                    # 로컬 이미지 목록
docker pull <image>              # 이미지 다운로드 (예: docker pull ubuntu:22.04)
docker rmi <image>               # 이미지 삭제
docker build -t <name> .         # Dockerfile로 이미지 빌드
docker search <keyword>          # Docker Hub 검색
```

## 컨테이너 실행
```bash
docker run <image>                       # 컨테이너 실행
docker run -d <image>                    # 백그라운드 실행 (detached)
docker run -it <image> /bin/bash         # 대화형 터미널로 실행
docker run -p 8080:80 <image>            # 포트 매핑 (호스트:컨테이너)
docker run -v /host/path:/container/path # 볼륨 마운트
docker run --name myapp <image>          # 컨테이너 이름 지정
docker run --rm <image>                  # 종료 시 자동 삭제
docker run -e KEY=VALUE <image>          # 환경변수 설정
```

## 컨테이너 관리
```bash
docker ps                  # 실행 중인 컨테이너 목록
docker ps -a               # 모든 컨테이너 목록 (중지 포함)
docker start <container>   # 중지된 컨테이너 시작
docker stop <container>    # 컨테이너 중지
docker restart <container> # 재시작
docker rm <container>      # 컨테이너 삭제
docker rm -f <container>   # 강제 삭제 (실행 중이어도)
```

## 컨테이너 접속/조사
```bash
docker exec -it <container> /bin/bash   # 실행 중인 컨테이너 접속
docker logs <container>                 # 로그 확인
docker logs -f <container>              # 실시간 로그 (follow)
docker inspect <container>              # 상세 정보 (JSON)
docker stats                            # 리소스 사용량 모니터링
docker top <container>                  # 컨테이너 내 프로세스
```

## 파일 전송
```bash
docker cp <container>:/path /host/path   # 컨테이너 → 호스트
docker cp /host/path <container>:/path   # 호스트 → 컨테이너
```

## 정리
```bash
docker system prune          # 사용하지 않는 리소스 정리
docker system prune -a       # 미사용 이미지까지 모두 삭제
docker volume prune          # 미사용 볼륨 삭제
docker network prune         # 미사용 네트워크 삭제
```

## Docker Compose (다중 컨테이너)
```bash
docker compose up -d         # 백그라운드로 서비스 시작
docker compose down          # 서비스 중지 및 삭제
docker compose ps            # 서비스 상태
docker compose logs -f       # 실시간 로그
docker compose restart       # 재시작
```

## 자주 쓰는 조합 예시
```bash
# Ollama 컨테이너 실행
docker run -d --name ollama -p 11434:11434 -v ollama:/root/.ollama ollama/ollama

# 모든 중지된 컨테이너 삭제
docker rm $(docker ps -aq -f status=exited)
```
