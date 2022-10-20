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

3. 내부적으로 malloc으로 메모리를 할당하는 함수는 함수명 앞에 new_를 붙인다.

	ex) ⭕️ 
	```C
	foo = new_sphere();
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

1. 조건문안 부정문을 지양, 긍정문 지향한다.

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


3. 비교를 할 때는 기준이 되는 값을 좌항에 둔다.

	ex) ❌
	```C
	if (42 > foo)
		return (~~~);

	```

	ex) ⭕️ 
	```C
	if (foo < 42)
		return (~~~);
