# FStringFormatter

### FString Format(const TCHAR* InExpression, const TMap<FString, FStringFormatArg>& InArgs) const

String Format에 맞추어 값을 형식화한다.

Format을 Key-Value 형식으로 대입할 수 있다.

```c++
TMap<FString, FStringFormatArg> Args;
Args.Add(TEXT("Key1"), TEXT("Replace 1"));
Args.Add(TEXT("Key2"), TEXT("Replace 2"));
FString::Format(TEXT("{Key1} {Key2}"), Args)
```

