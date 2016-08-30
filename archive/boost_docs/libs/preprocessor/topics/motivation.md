#ư��

C++ �δؿ���ƥ�ץ졼�Ȥΰ����ꥹ�Ȥ����̤ʹ�ʸ�ˤ�ä��Ȥ�Ω�Ƥ����Τǡ�C++ �μ��ˤ�äƹ���������������Ǥ��ʤ���
���Τ��Ȥˤ�äƥ����ɤ�̵�̤�ȿ�����Ƥ��ޤ����Ȥ����롣

��Ȥ���Boost�� `is_function<>` �᥿�ؿ��μ����򸫤Ƥߤ褦��
���μ����ϡ������ؿ��ؤΥݥ��󥿤��Ѵ��Ǥ��뤫�ɤ�����Ĵ�٤� `is_function_tester()` ¿������ؿ���ȤäƤ��롣
�����ꥹ�Ȥ����̤ʼ谷��������뤿�ᡢǤ�ոĤΰ�������Ĵؿ���ľ�ܥޥå������뤳�ȤϤǤ��ʤ���
���Τ����ˡ��ؿ� `is_function_tester()` �ϥ��ݡ��Ȥ�������Ƥΰ����θĿ����Ȥ��̡����������ʤ���Фʤ�ʤ���
�㤨�м����̤�:

```cpp
template<class R>
yes_type is_function_tester(R (*)());

template<class R, class A0>
yes_type is_function_tester(R (*)(A0));

template<class R, class A0, class A1>
yes_type is_function_tester(R (*)(A0, A1));

template<class R, class A0, class A1, class A2>
yes_type is_function_tester(R (*)(A0, A1, A2));

// ...
```

���Τ褦�ʼ���η����֤������Ū�ʥ���ݡ��ͥ�Ȥ�᥿�ץ���ߥ󥰤Τ���ε�ǽ�μ����򤹤�ݤ����ˤ˵����롣

##ŵ��Ū�ʲ��ˡ

ŵ��Ū�ˤϡ����Τ褦�ʷ����֤��ϼ�ư�ǲ�褵��롣
��ư�ˤ�뷫���֤�������Ū�ǤϤʤ�������������Ƥ��ʤ��ʹ֤��ܤˤϤ��Τ褦�ʥ����ɤ��ɤߤ䤹�����Ȥ����롣

�ۤ��β��ˡ�Ȥ��Ƥϡ������֤����������볰���ץ�����Ȥ����Ȥ䡢���٤ʥ��ǥ����ʤɤ�Ȥ���ˡ�����롣
��ǰ�ʤ��顢�����������ץ�����Ȥ���ˡ�Ϥ�������η���������:

- �����ץ�����񤯤Τϻ��֤������롣(ɸ��Ū�������ץ�����Ȥ��ȳڤˤʤ뤬��)
- �������줿 C++ �����ɤ�ľ���ѹ��Ǥ��ʤ���
- �����ץ�����Ƥ֤Τ��񤷤����⤷��ʤ���
- ����δĶ��ˤ����Ƥ������ץ����θƤӽФ���ư������Τ��񤷤����⤷��ʤ���
	(�ƤӽФ��μ�ư�������ˤ��ѹ������饤�֥��ˤȤäƤ�̥��Ū�Ǥ��롣)
- �����ץ����ΰܿ������ۤ��񤷤����⤷��ʤ��������֤���񤹤롣

##�ץ�ץ��å��ǤϤɤ�����

C++�ˤϥץ�ץ��å����դ��Ƥ���Τǡ����Τ褦�ʼ��פ˸����Ƥ���ȹͤ��뤫�⤷��ʤ���
�ºݡ��ץ�ץ��å��Ϥ��Τ褦�ʥ������˶ˤ�������Ǥ��롣�ʤ��ʤ�:

- �ץ�ץ��å��ϥݡ����֥�Ǥ��롣
- �ץ�ץ��å��ϥ���ѥ���ΰ����Ȥ��Ƽ�ưŪ�˼¹Ԥ���롣
- �ץ�ץ��å��Υ����ɤ�ľ�� C++ �Υ����ɤ������ळ�Ȥ��Ǥ��롣
- ����ѥ�����̾�ץ�ץ��å��ν��Ϥ򸫤뤳�Ȥ��Ǥ���褦�ˤʤäƤ��뤬��������������줿�����ɤ�ǥХ������ꥳ�ԡ�����Τ������Ǥ��롣

��ǰ�ʤ���ץ�ץ��å����������٥�ʤ�ΤǤ��ꡢ�����֤���Ƶ�Ū�ޥ���򥵥ݡ��Ȥ��Ƥ��ʤ���
�������äƥ饤�֥��ˤ�륵�ݡ��Ȥ�ɬ�פǤ��롣

- �ܺ٤ʥץ�ץ��å��ε�ǽ�����¤ˤĤ��Ƥϡ�C++ ɸ�� [[Std]](bibliography.md#std) �򻲾Ȥ��Ƥۤ�����

##�դ����������

�ץ�ץ��å��饤�֥�����Ѥ���ȡ� `is_function_tester()` �ϼ��Τ褦�˼����Ǥ���:

```cpp
#define IS_FUNCTION_TESTER(Z, N, _) \
	template<class R BOOST_PP_COMMA_IF(N) BOOST_PP_ENUM_PARAMS(N, class A)> \
	yes_type is_function_tester(R (*)(BOOST_PP_ENUM_PARAMS(N, A))); \
	/**/

BOOST_PP_REPEAT(BOOST_PP_INC(MAX_IS_FUNCTION_TESTER_PARAMS), IS_FUNCTION_TESTER, _)

#undef IS_FUNCTION_TESTER
```

���ݡ��Ȥ�������κ���Ŀ����ѹ�����ˤϡ�ñ�� `MAX_IS_FUNCTION_TESTER_PARAMS` ���ѹ����ƥ���ѥ��뤷�ʤ����Ф褤��

---

(C) Copyright [Housemarque Oy](http://www.housemarque.com) 2002

Permission to copy, use, modify, sell and distribute this document is granted provided this copyright notice appears in all copies.
This document is provided "as is" without express or implied warranty and with no claim as to its suitability for any purpose.

