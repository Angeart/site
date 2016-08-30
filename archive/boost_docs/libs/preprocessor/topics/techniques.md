#�ƥ��˥å���

�ץ�ץ��å��᥿�ץ���ߥ󥰤ε����㼨���롣

##�� - �����ʵ��Ϥ�ȿ�����򤱤뤿��˶ɽ�Ū�ʥޥ����Ȥ���

```cpp
#define BOOST_PP_DEF(op) /* ..................................... */  \
	template<class T, int n>                                          \
	vec<T, n> operator op ## =(vec<T, n> lhs, const vec<T, n>& rhs) { \
		for (int i = 0; i &lt; n; ++i) {                              \
			lhs(i) op ## = rhs(i);                                    \
		}                                                             \
	}                                                                 \
	/**/

BOOST_PP_DEF(+)
BOOST_PP_DEF(-)
BOOST_PP_DEF(*)
BOOST_PP_DEF(/)

#undef BOOST_PP_DEF
```

###����:

�̾�Ϥ��Τ褦�ʼ���Υ����ɤ��Ф��� `BOOST_PP_DEF` �Τ褦��ɸ��Ū�ʥޥ����̾����Ȥäƹ���ʤ���
�ʤ��ʤ餳�Υޥ���ϻ��Ѥ������Τ������Ф��������դ�����̤����ˤ���Ƥ��뤫�顣

###����:

��³�Ԥ����������Ѥ���Ƥ��뤫��ǧ���䤹������ˤϷ�³ʸ��(�Хå�����å���ʸ��)�ΰ��֤�·����Ȥ褤��

###���:

�̤α黻�Ҥ�������뤳�Ȥˤ�äƤ�������ĥ���뤳�Ȥ��Ǥ��롣
����򤹤����ˡ�*algebraic categories* (ʸ�� [[Barton]](bibliography.md#barton) �ǾҲ𤵤�Ƥ���)�� *layered architecture* (�㤨��ʸ�� [[Czarnecki]](bibliography.html#czarnecki)) ��Ȥ����Ȥ��θ���衣
�������ʤ��顢�黻�ҥȡ����� `*`, `/`, `+`, `-`, ���ϥƥ�ץ졼�Ȥˤ�äƤ������Ǥ��ʤ����顢�����Υȡ������ɤ����˽�ɬ�פ��Ф���������
���Υȡ������ȿ��(*categorical repetition*)�ϥƥ�ץ졼�ȥ᥿�ץ���ߥ󥰤ˤ�äƽ���Ǥ��롣

##�� - �ޥ��� BOOST_PP_EMPTY ��ɽ�Ū�ʥޥ���Υ��󥹥��󥹲��κݤ�̤���ѥѥ�᡼���Ȥ��ƻ��Ѥ��롣

```cpp
#define BOOST_PP_DEF(cv) /* ... */ \
	template<class base>           \
	cv() typename implement_subscript_using_begin_subscript<base>::value_type& \
	implement_subscript_using_begin_subscript<base>::operator[](index_type i) cv() { \
		return base::begin()[i];   \
	}                              \
	/**/
```

###���Ȥ�:

`BOOST_PP_EMPTY()` �϶���Ÿ�������Τ�̤���ѥѥ�᡼���Ȥ��ƻ��Ѥ��뤳�Ȥ��Ǥ��롣

###���:

`BOOST_PP_EMPTY` �θ��� () ���դ��ʤ���Ÿ������ʤ���

�ؿ��Τ褦�ʥޥ����Ƥ֤ˤ� () ��ɬ�פǤ��롣

###�ٹ�:

`BOOST_PP_EMPTY()` ��ȤäƤ����硢 Ϣ��(concatenation)�ϰ����˻��ѤǤ��ʤ���

###����:

���ޡ�1���2�Ԥ�¾�ιԤ���ü��Ĺ���ʤ뤳�Ȥ����롣
��³�Ա黻�Ҥΰ��֤����ƤιԤˤĤ���·���뤳�Ȥ� *���ʤ�* ���Ȥˤ�äơ��������򤽤�ۤɵ����ˤ����˺�Ȥ�ڤˤ��뤳�Ȥ��Ǥ��롣

###����:

�ץ�ץ��å��᥿�ץ���ߥ󥰤Τ���Υޥ����̻Ҥ�ϥ��饤��ɽ������:

- `BOOST_PP_DEF`
- `BOOST_PP_EMPTY`
- `BOOST_PP_REPEAT`
- ...

����ˤ�äƲ����������夹�롣

##�� - ɬ�פʤ� ## �Τ����� BOOST_PP_CAT ��Ȥ���

```cpp
#define STATIC_ASSERT(expr) \
	enum { BOOST_PP_CAT(static_check_, __LINE__) = (expr) ? 1 : -1 }; \
	typedef char \
		BOOST_PP_CAT(static_assert_, __LINE__)[BOOST_PP_CAT(static_check_, __LINE__)] \
	/**/

// ...

STATIC_ASSERT(sizeof(int) <= sizeof(long));
```

###��ͳ:

�ޥ���Ÿ����(�ؾ���)�Ƶ�Ū��Ŭ�Ѥ���롣
�ȡ�����η��ϥޥ���Ÿ�����˳����롣
���Τ���ȡ�����η����ٱ䤻�ͤФʤ�ʤ����Ȥ����Ф��е����롣

##�� - ɬ�פʤ� # �Τ����� BOOST_PP_STRINGIZE ��Ȥ���

```cpp
#define NOTE(str) \
	message(__FILE__ "(" BOOST_PP_STRINGIZE(__LINE__) ") : " str) \
	/**/

// ...

#pragma NOTE("TBD!")
```

###��ͳ:

�ޥ���Ÿ����(�ؾ���)�Ƶ�Ū��Ŭ�Ѥ���롣
ʸ���󲽤ϥޥ���Ÿ�����˳����뤿�ᡢʸ���󲽤��ٱ䤻�ͤФʤ�ʤ����Ȥ����Ф��е����롣

##�� - BOOST_PP_ENUM_PARAMS (�䤽���Ѽ�)�� BOOST_PP_REPEAT �� BOOST_PP_COMMA_IF ����Ȥäƥꥹ������ *O*(*n*) �����֤������롣

```cpp
struct make_type_list_end;

template<
	BOOST_PP_ENUM_PARAMS_WITH_A_DEFAULT(
		MAKE_TYPE_LIST_MAX_LENGTH, 
		class T, 
		make_type_list_end
	)
>
struct make_type_list {
private:
	enum { end = is_same&lt;T0, make_type_list_end&gt;::value };
public:
	typedef typename type_if<
		end, type_cons_empty,
		type_cons<
			T0,
			typename type_inner_if<
				end, type_identity<end>,
				make_type_list<
					BOOST_PP_ENUM_SHIFTED_PARAMS(
						MAKE_TYPE_LIST_MAX_LENGTH,
						T
					)
				>
			>::type
		>
	>::type type;
};
```

###���Ȥ�:

`BOOST_PP_REPEAT` �ϺƵ���ɤ�����Ѥ��� (����������):

```cpp
#define BOOST_PP_REPEAT(n, m, p) BOOST_PP_REPEAT ## n(m, p)

#define BOOST_PP_REPEAT0(m, p)
#define BOOST_PP_REPEAT1(m, p) m(0, p)
#define BOOST_PP_REPEAT2(m, p) m(0, p) m(1, p)
#define BOOST_PP_REPEAT3(m, p) BOOST_PP_REPEAT2(m, p) m(2, p)
#define BOOST_PP_REPEAT4(m, p) BOOST_PP_REPEAT3(m, p) m(3, p)
// ...
```

###���:

*��Υ����ɤϷ褷�� `BOOST_PP_REPEAT` �μ����ʤɤǤϤʤ���ñ�������Τ���Τ�ΤǤ��롪*

`BOOST_PP_ENUM_PARAMS` �Ȥ����Ѽ�� `BOOST_PP_REPEAT` ��ȤäƤ��롣
`BOOST_PP_COMMA_IF(I)` �� I != 0 �ΤȤ�����ޤ�Ÿ������롣
`BOOST_PP_INC(I)` ���ܼ�Ū�ˤ� "I+1" ��Ÿ�����졢`BOOST_PP_DEC(I)` �� "I-1" ��Ÿ������롣

##�� - �����¤����ΤǤϤʤ���*����դ��Υޥ������* ��Ȥäơ�ɬ�פ˱����ƥ桼���������ɤη����֤�������Ǥ���褦�ˤ��롣

```cpp
#ifndef MAKE_TYPE_LIST_MAX_LENGTH
#define MAKE_TYPE_LIST_MAX_LENGTH 8
#endif
```

���Τ褦�ˤ���С��饤�֥��Υ����ɤ��ѹ����뤳�Ȥʤ��桼���� `make_type_list` �����ꤹ�뤳�Ȥ��Ǥ��롣

##�� - BOOST_PP_REPEAT �� *�ȡ�����ȹ�ؿ�* ��Ȥä� categorical repetition �����롣

```cpp
// ���: ��Υ���ѥ���ϻ��ѷ��˴ؤ���ɸ��Ū�ǤϤʤ���
#define ARITHMETIC_TYPE(I) ARITHMETIC_TYPE ## I

#define ARITHMETIC_TYPE0    bool
#define ARITHMETIC_TYPE1    char
#define ARITHMETIC_TYPE2    signed char
#define ARITHMETIC_TYPE3    unsigned char
#define ARITHMETIC_TYPE4    short
#define ARITHMETIC_TYPE5    unsigned short
#define ARITHMETIC_TYPE6    int
#define ARITHMETIC_TYPE7    unsigned int
#define ARITHMETIC_TYPE8    long
#define ARITHMETIC_TYPE9    unsigned long
#define ARITHMETIC_TYPE10   float
#define ARITHMETIC_TYPE11   double
#define ARITHMETIC_TYPE12   long double

#define ARITHMETIC_TYPE_CNT 13

// ...

#define BOOST_PP_DEF(z, I, _) /* ... */ \
	catch (ARITHMETIC_TYPE(I) t) {      \
		report_typeid(t);               \
		report_value(t);                \
	}                                   \
	/**/

BOOST_PP_REPEAT(ARITHMETIC_TYPE_CNT, BOOST_PP_DEF, _)

#undef BOOST_PP_DEF
```

###���:

�����η����֤��ϥƥ�ץ졼�ȥ᥿�ץ���ߥ� [[Czarnecki]](bibliography.html#czarnecki) �ˤ�äƤ����Ǥ��롣
�������ʤ���黻�ҥȡ������ categorical repetition �ϥƥ�ץ졼�ȥ᥿�ץ���ߥ󥰤ˤ�äƤϴ����˽���Ǥ��ʤ���

##�� - BOOST_PP_REPEAT ��Ȥä�*O*(*n* * *n*)�η����֤������롣

```cpp
#ifndef MAX_VEC_ARG_CNT
#define MAX_VEC_ARG_CNT 8
#endif

// ...

#define ARG_FUN(z, i, _) BOOST_PP_COMMA_IF(i) T a ## i
#define ASSIGN_FUN(z, i, ) (*this)[i] = a ## i;

#define DEF_VEC_CTOR_FUN(z, i, _) /* ... */ \
	vec(BOOST_PP_REPEAT(i, ARG_FUN, _)) {   \
		BOOST_PP_REPEAT(i, ASSIGN_FUN, _)   \
	}                                       \
	/**/

BOOST_PP_REPEAT(BOOST_PP_INC(MAX_VEC_ARG_CNT), DEF_VEC_CTOR_FUN, _)

#undef ARG_FUN
#undef ASSIGN_FUN
#undef DEF_VEC_CTOR_FUN

// ...
```

###���Ȥ�:

`BOOST_PP_REPEAT` �� *��ư�Ƶ�* [����: ???]�򵯤�������褦�����̤���ˡ�Ǽ�������Ƥ��롣

##�� - BOOST_PP_IF ��Ȥä�ʬ����¸����롣

```cpp
#define COMMA_IF(c) \
	BOOST_PP_IF(c, BOOST_PP_COMMA, BOOST_PP_EMPTY)() \
	/**/

BOOST_PP_IF(0, true, false) == false;
BOOST_PP_IF(1, true, false) == true;
```

`BOOST_PP_IF` ��Ȥ��� `BOOST_PP_REPEAT` ��Ȥä��ꥹ�Ȥ��������ñ�ˤǤ��롣

###���:

*THEN* �� *ELSE* ����ʬ(��2����3����)�ϥޥ���Ǥ���ɬ�פϤʤ���
���������⤷�����ΰ������ؿ�Ū�ʥޥ���Ǥ��äơ���������դ���Ÿ���������ΤǤ���С��⤦������ؿ�Ū�ޥ���ˤ��ʤ���Фʤ�ʤ���
������Ū�Τ���� `BOOST_PP_IDENTITY` ��Ȥ����Ȥ��Ǥ��롣
������ (Aleksey Gurtovoy �ˤ��) �򸫤�:

```cpp
#define NUMBERED_EXPRESSION(i, x) /* ... */ \
	BOOST_PP_IF(                            \
		i,                                  \
		BOOST_PP_IDENTITY(x ## i)           \
		BOOST_PP_EMPTY                      \
	)()                                     \
	/**/
```

###���:

��� `COMMA_IF` ����Τ褦�ˡ�`BOOST_PP_IF` �η�̤��ƤФ�Ƥ� *THEN* �� *ELSE* �ѥ�᡼�����ƤФ�ʤ����Ȥ����롣
�⤷�ѥ�᡼����ƤФ��ʤ顢`BOOST_PP_IF` ��Ŭ�ڤ�Ÿ����������� `BOOST_PP_EMPTY` ������Ÿ������뤿�ᡢ���Υ����ɤ�������Ÿ������ʤ��ʤäƤ��ޤ���
[����: ???]

###���Ȥ�:

`BOOST_PP_IF` �����Ƥη����֤��ϰϤˤĤ����������Ƥ���(����������):

```cpp
#define BOOST_PP_IF(c, THEN, ELSE) BOOST_PP_IF ## c(THEN, ELSE)

#define BOOST_PP_IF0(THEN, ELSE) ELSE
#define BOOST_PP_IF1(THEN, ELSE) THEN
#define BOOST_PP_IF1(THEN, ELSE) THEN
// ...
```

##��: ���ѡ���������ӱ黻��Ȥ���

```cpp
#define SPECIAL_NUMBERED_LIST(n, i, elem, special) \
	BOOST_PP_ASSERT_MSG(                      \
		BOOST_PP_LESS(i, n),                  \
		bad params for SPECIAL_NUMBERED_LIST! \
	)                                         \
	BOOST_PP_ENUM_PARAMS(i, elem)             \
	BOOST_PP_COMMA_IF(i) special              \
	BOOST_PP_REPEAT(                          \
		BOOST_PP_SUB(BOOST_PP_DEC(n), i),     \
		SPECIAL_NUMBERED_LIST_HELPER,         \
		(elem, i)                             \
	)                                         \
	/**/

#define SPECIAL_NUMBERED_LIST_HELPER(z, i, elem_base) \
	,                                            \
	BOOST_PP_CAT(                                \
		BOOST_PP_TUPLE_ELEM(2, 0, elem_base),    \
		BOOST_PP_ADD(                            \
			i,                                   \
			BOOST_PP_TUPLE_ELEM(2, 1, elem_base) \
		)                                        \
	)                                            \
	/**/

SPECIAL_NUMBERED_LIST(3, 0, E, S)
SPECIAL_NUMBERED_LIST(3, 1, E, S)
SPECIAL_NUMBERED_LIST(3, 2, E, S)
SPECIAL_NUMBERED_LIST(3, 3, E, S)
```

---

(C) Copyright [Housemarque Oy](http://www.housemarque.com) 2002

Permission to copy, use, modify, sell and distribute this document is granted provided this copyright notice appears in all copies.&nbsp;
This document is provided "as is" without express or implied warranty and with no claim as to its suitability for any purpose.

