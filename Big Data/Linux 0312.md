<pre>[hadoop@hadoop01 ~]$ sqoop export -connect jdbc:oracle:thin:@70.12.115.64:1521:xe -username shop -password shop -export-dir /mywork/cmdwordcount6/part-r-00000 -table comment_result -columns &quot;word, count&quot; --fields-terminated-by &quot;\\t&quot;
</pre>

* --fields-terminated-by <char>

   : <char>를 기준으로 잘라서 컬럼으로 구분시켜 준다.

   &quot;\\t" : sqoop 안에서 \를 사용하기 때문에 두번 `\\ ` 붙여주어야 한다.

​	



















프로젝트에서 어떻게 구현했는지...

내가 구현했든 안했든 프로젝트 모든 부분 파악하기

