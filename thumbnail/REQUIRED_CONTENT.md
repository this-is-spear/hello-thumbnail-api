# 클라이언트 썸네일 관리 서비스

## 개요

썸네일을 사이즈별로 S3에 관리한다면 요구되는 용량이 기하급수적으로 많아지게 됩니다.
요청된 이미지에 따라 리사이징한다면 요구되는 용량을 줄일 수 있습니다.

클라이언트에서 사용하는 이미지는 대부분 동일한 요청을 띄게 됩니다. 

## 요구사항

- 팀원은 이미지를 업로드해서 원하는 사이즈의 이미지를 사용자들에게 제공 할 수 있다.

## 프로그래밍 요구사항

- 이미지 식별자와 사이즈를 입력받아 리사이징 후 반환한다.

## 서비스 흐름

1. 팀원은 이미지를 업로드한다.
2. 팀원은 이미지 주소를 얻는다.
3. 팀원은 이미지와 이미지 이름 이미지 주소가 포함된 리스트를 얻는다.
4. 사용자는 이미지 식별자와 사이즈를 입력해 리사이즈된 이미지를 반환받는다.

## 모델링

### UploadController

- 팀원은 이미지 파일 리스트를 입력해 업로드한다.(`uploadImages`)
  - 이미지 이름은 고유해야 한다.
  - 이미지 파일은 비어있을 수 없다.
  - 이미지 리스트를 업로드 한다.
  - 업로드된 이미지 경로를 반환한다.

### UploadService

- 이미지 리스트를 가져와 업로드 한다.
  - 이미지 파일 최대 크기는 `10MB`다.
  - 이미지를 저장한다.

### FileUploader

- 이미지를 업로드한다.

### S3FileUploader

- S3에 파일을 업로드한다.

