#### [axios.delete](https://github.com/axios/axios/issues/736)
```javascript
delete의 params은 {data: params} 처럼 data로 지정해야 한다.


function* deleteNotice(action) {
	const { payload } = action;
	const { databaseUrl } = config;
	const url = `${databaseUrl}/notice`;
	const params = { ...payload };
	const headers = { headers: { 'Content-Type': 'application/json' } };
	try {
		const res = yield axios.delete(url, { data: params }, headers);
		const { data } = res;
		console.log(res);
		yield put({ type: 'DELETE_NOTICE_SUCCESS', payload: data });
	} catch (err) {
		console.log(err);
	}
}
```