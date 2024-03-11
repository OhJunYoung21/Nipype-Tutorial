## BIDS Validator issue

~~~unix
fmriprep-docker <input-file> <output_file> <participant>
~~~

다음과 같은 형태로 데이터를 사용하려고 하였으나, 내가 사용하는 데이터가 bids_validated가 되어 있지 않다는 오류가 발생하였다. 주로 오류는 .json파일에서 발생하였으며 이를 해결하기 위해 처음부터 BIDS_validated 가 valid상태인 데이터를 다운받고자 한다.

### Error 1: [Code 90] SIDECAR_WITHOUT_DATAFILE

출력되는 에러메세지는 위와 같다.
