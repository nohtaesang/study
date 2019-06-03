#### [s3 에서 특정 폴더안에 있는 파일 가져오기]
```javascript
s3.listObjectsV2(
	{
		Bucket: 'dexnetworks',
		Prefix: 'popupImages'
	},
	(err, data) => {
		if (err) {
			throw err;
		}
		console.log(data.Contents);
		
	}
);

가져오는 순서는 최신순이 아닌 알파벳 순서이다
```
#### [s3 파일 관리를 위한 aws-sdk 활용법](https://mygumi.tistory.com/320)
```
s3는 일반적인 파일 시스템이 아닌 key-value 형태와 같은 객체 스토리지이다.

```
#### [vscode 에서 credential 설정하기]
```
package에서 aws cli 설치
create credential prifile 로 access_key와 secret_key를 설정,
open credntial and config file 로 파일 열고 region 추가

[nohtaesang]
region=ap-northeast-2
aws_access_key_id= [access_key]
aws_secret_access_key= [secret_key]
```
#### [s3 란](https://aws.amazon.com/ko/s3/faqs/#Durability_.26_Data_Protection)
#### [aws toolkit for visual studio code 설치하기](https://docs.aws.amazon.com/ko_kr/toolkit-for-vscode/latest/userguide/setup-toolkit.html)

#### [s3에서 객체 지우기 - restful api](https://stackoverflow.com/questions/27753411/aws-s3-delete-object-using-javascript)

