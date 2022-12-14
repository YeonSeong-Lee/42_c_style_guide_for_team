# 42_c_style_guide_for_team
c coding style guide for 42 team project

free to use it, and happy team project!


## malloc

1. malloc 안에서 크기를 계산할 때, `sizeof`를 먼저 쓴다. 

	ex) ❌
	```C
	scene = malloc(42 * sizeof(t_scene));
	```

	ex) ⭕️ 
	```C
	scene = malloc(sizeof(t_scene) * 42);
	```

2. malloc앞에 자료형을 붙이지 않는다. 

	ex) ⭕️ 
	```C
	scene = malloc(sizeof(t_scene));
	```

---

## function name

1. 함수이름은 동사로 시작한다. 

	ex) ❌
	```C
	flag = space_checker();
	```

	ex) ⭕️ 
	```C
	flag = is_space();
	```

2. 객체를 생성하는 생성자 함수는 객체이름으로 한다.

	ex) ⭕️ 
	```C
	new_sphere()
	```

3. 내부적으로 malloc으로 메모리를 할당하는 함수는 함수명 앞에 `new_`를 붙인다.

	ex) ⭕️ 
	```C
	foo = new_sphere();
	```

---

## return

1. return 값은 가능한 단순하게 유지한다. 

	ex) ❌
	```C
	return (vmin(vmult_(light_color, scene->rec.albedo), color3(1, 1, 1)));
	```

	ex) ⭕️ 
	```C
	return (min_light)
	```

2. if else 보다는 early return을 선호한다.

	ex) ❌
	```C
	if (___)
	{
		return (~~~);
	}
	else 
	{
		return (~~);
	}
	```


	ex) ⭕️ 
	```C
	if (__)
		return (~~~);
	return (~~);
	```

---

## if, 조건문

1. 조건문안에서 부정문을 지양, 긍정문을 지향한다.

	ex) ❌
	```C
	if (foo != TRUE)
		return (~~~);

	```

	ex) ⭕️ 
	```C
	if (foo == FALSE)
		return (~~~);
	```


2. 조건문안에 비교하는 값 명시한다.

	ex) ❌
	```C
	if (!foo)
		return (~~~);

	```

	ex) ⭕️ 
	```C
	if (foo == FALSE)
		return (~~~);
	```


3. 비교를 할 때는 비교가 되는 값을 좌항에 둔다.

	ex) ❌
	```C
	if (42 > foo)
		return (~~~);

	```

	ex) ⭕️ 
	```C
	if (foo < 42)
		return (~~~);

4. 가능한 if 중첩을 피한다.

	ex) ❌
	```C
	if (foo == TRUE)
	{
		if (bar == TRUE)
		{
			return (~~~);
		}
	}
	```

	ex) ⭕️ 
	```C
	if (foo == TRUE && bar == TRUE)
		return (~~~);
	```

## while, 반복문

1. 포인터 연산을 통한 순환보다 인덱스를 이용한 순회를 선호한다.


	ex) ❌ 
	```C
	while(foo != NULL)
	{
		bar = *foo;
		~~
		++foo;
	}
	```

	ex) ⭕️
	```C
	while(foo[i] != NULL)
	{
		bar = foo[i];
		~~
		++i;
	}
	```

2. 증감연산자는 조건문안에 넣지 않는다.

	ex) ❌
	```C
	while(++i < 42)
	{
		~~
	}
	```

	ex) ⭕️ 
	```C
	while(i < 42)
	{
		~~
		++i;
	}
	```
3. 전위연사자를 후위연산자보다 선호한다.

	ex) ❌
	```C
	while(i < 42)
	{
		~~
		i++;
	}
	```

	ex) ⭕️ 
	```C
	while(i < 42)
	{
		~~
		++i;
	}
	```

---

## 변수선언

1. `const`를 선언할 수 있으면 선언부터
