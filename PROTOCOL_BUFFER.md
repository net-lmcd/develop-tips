# Protocol Buffer 

프로토콜 버퍼는 구글에서 개발하고 공개한 오픈소스로, **직렬화 데이터 구조(Serialized Data Structure)**이다. Java, Python, Object C, Javascript, Ruby등 다양한 언어를 지원하며 특히 직렬화 속도가 빠르고, 직렬화된 파일 크기도 작아 많이 사용된다.

**직렬화란? -  Data를 파일로 저장하거나 네트워크로 전송하기 위해 Binary Stream 형태로 저장하는 행위이다.

 gRPC 프로토콜의 경우 HTTP 2.0을 기반으로 하며, 이 프로토콜 버퍼를 이용하여 메시지를 직렬화 시키므로, 프로토콜 버퍼를 이해하면 gRPC를 습득하는것이 상대적으로 쉽다. 

- 1. 프로토콜 버퍼는 하나의 파일에 최대 64M까지 지원할 수 있으며, 
- 2. Json 파일 -> 프로토콜 버퍼 파일 포맷으로 변환 가능.
- 3. 프로토콜 버퍼 파일 -> Json으로 전환 가능

# 구조 및 사용방법
- 프로토콜 버퍼를 사용하기 위해서는 저장하기 위한 데이터형을 **proto file**이라는 형태로 정의한다. 프로토콜 버퍼는 여러 언어를 지원하므로, 특정 언어에 종속되지 않는 형태로 데이터 타입을 정의해야한다. 
**이걸 proto file**이라 한다. 

이렇게 정의된 데이터 타입을 프로그래밍 언어에서 사용하려면, 해당 언어에 맞는 형태의 데이터 클래스로 생성해야 한다. 

 protoc 컴파일러로 proto file을 컴파일하면, 각 언어에 맞는 형태의 데이터 클래스 파일을 생성해준다. 

Proto file(*.proto) -> Compile -> Soruce file(*.java, *.py)
이렇게 생성된 데이터 파일을 프로그래밍 언어에서 불러 데이터 클래스를 사용하면 된다.

# Style Guide
This document provides a style guide for .proto files. By following these conventions, you'll make your protocol buffer message definitions and their corresponding classes consistent and easy to read.

## Message And Field Names
Use CamelCase (with an initial capital) for message names – for example, SongServerRequest. Use underscore_separated_names for field names – for example, song_name.

message SongServerRequest {
  required string song_name = 1;
}
Using this naming convention for field names gives you accessors like the following:

### C++:
  const string& song_name() { ... }
  void set_song_name(const string& x) { ... }

### Java:
  public String getSongName() { ... }
  public Builder setSongName(String v) { ... }
This document provides a style guide for .proto files. By following these conventions, you'll make your protocol buffer message definitions and their corresponding classes consistent and easy to read.

## Message And Field Names
Use CamelCase (with an initial capital) for message names – for example, SongServerRequest. Use underscore_separated_names for field names – for example, song_name.

message SongServerRequest {
  required string song_name = 1;
}
Using this naming convention for field names gives you accessors like the following:

### C++:
  const string& song_name() { ... }
  void set_song_name(const string& x) { ... }

### Java:
  public String getSongName() { ... }
  public Builder setSongName(String v) { ... }
