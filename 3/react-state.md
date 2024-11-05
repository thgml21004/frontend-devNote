# React State

#### Effect 이렇게 쓰지 말기&#x20;

```
function Form() {
  const [firstName, setFirstName] = useState('Taylor');
  const [lastName, setLastName] = useState('Swift');

  // 🔴 Avoid: redundant state and unnecessary Effect
  const [fullName, setFullName] = useState('');
  useEffect(() => {
    setFullName(firstName + ' ' + lastName);
  }, [firstName, lastName]);
  // ...
}
```

#### toggle 버튼은 이렇게 작성 (!)

```
const toggleDarkMode = () => {
    setIsDarkMode(!prevMode);
};
```
