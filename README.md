# SQL
addBookMySQL 테스트 해보기

## 1. 라이브러리 설치
```bash
pip install pymysql
pip install PyQt5
```

## 2. MySQL 서버에 연결을 시도

`host`: 데이터베이스 서버 주소 (IP 또는 도메인)

`user`: DB 접속 계정

`passwd`: 비밀번호

`db`: 사용할 데이터베이스 이름

`charset`: 인코딩 (한글 깨짐 방지를 위해 utf8 사용)

`port`: MySQL 서버 포트

`cursorclass`: 커서 반환 형태 설정 (DictCursor는 결과를 딕셔너리로 반환)

```
self.connection = pymysql.connect(
            host = 'bitnmeta2.synology.me',
            user = 'iyrc',
            passwd = 'Dodan1004!',
            db = 'test_sa',
            charset = 'utf8',
            port = 3307,
            cursorclass = pymysql.cursors.DictCursor)
```
## 2-1. MySQL 서버
<img src="https://github.com/user-attachments/assets/2baee166-7693-4597-a5eb-2df171ad2c61" width="900" height="300"/>

## 3. 기능 설명 

`insert()`:	이름과 전화번호 삽입

`update()`:	전화번호 수정	

`delete()`:	이름 기준 삭제

`search()`:	이름 또는 전화번호 검색

`pause()`:	테스트 중 일시정지

```
if __name__ == '__main__':
    app = QApplication(sys.argv)
    db = mysqlDB()
    # 추가 테스트
    result = db.insert("홍길동fromPython","010,0987,6543")
    print("Insert test: ", result)   
    result = db.insert("홍길동2","011-1234-6543")
    print("Insert test: ", result)   
    db.pause()

    # 수정 테스트
    result = db.update("홍길동fromPython","010-4333-1212")
    print("Update Test : ", result)
    db.pause()

    # 찾기 테스트
    result = db.search("홍")
    print("Search Test : ", result)
    db.pause()

    # 삭제 테스트
    result = db.delete("홍길동fromPython")
    print("Delete Test : ", result)

    exit(app.exec_())
```

## 4. 실행
![image](https://github.com/user-attachments/assets/a6ab71b2-2d16-4342-b449-ea4610e86aa6)

