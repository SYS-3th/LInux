# 쉘 조건,반복문

## if문

```
if [값 조건식 값 조건식...]
then
    수행문
elif [값 조건식 값 조건식...]
then
    수행문
else
    수행문
fi
```

## case문
```
case "$1" in
  start)
        echo "시작~~";;
  stop)
        echo "중지~~";;
  restart)
        echo "다시 시작~";;
  *)
        echo "뭔지 모름~~";;
esac
exit 0
```
## for
```
for [변수] in [반복 조건]
do
    [실행문]
done
```
## while문
```
while [ 값1 조건식 값2 ]
do
   [실행문]
   [실행문]
done 
```
