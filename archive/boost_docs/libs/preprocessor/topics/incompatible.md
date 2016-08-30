#��ߴ���

������ Boost �Υ�꡼��(1.28)�ȤϤ����Ĥ���ߴ�����ʬ�����롣
�������绨�Ĥ˸��äƻ��ĤΥ��ƥ���ˤ櫓���롣

- `BOOST_PP_REPEAT` �˴�Ť���ʿȿ��
- ������ʸ
- *list* �ξ��߹���

##ȿ���������å�

�ޤ����Ǥ⹭���Ȥ��Ƥ���Ȼפ���Τϡ�`BOOST_PP_REPEAT` ���Ϥ���륿�����åȥޥ���ȡ�`BOOST_PP_REPEAT` ��Ȥä���ʿȿ���ι����Ǥ��롣
����ϥ������åȥޥ����ɬ�פȤ���褦�����Ƥ� `BOOST_PP_REPEAT_*` �����Ƥ� `BOOST_PP_ENUM_*` ��ޤࡣ

��ߴ����ϼ����Ǥ��뤬������ϥ��������ѹ���ɬ�פȤ��롣

�����Υ������åȥޥ���� *��3��* ��������Ԥ���褦�ˤʤä���
�ɲä��줿�Τϳƥ������åȥޥ���� *�ǽ��* �ѥ�᡼���Ǥ��롣
It represents the next repetition dimension and brings `BOOST_PP_REPEAT` inline with rest of the library.

�������äƼ��Τ褦�Ǥ��ä���Τ�:

```cpp
#define macro(n, data) ...
BOOST_PP_REPEAT(5, macro, data)
```

...���Τ褦�ˤʤ�:

```cpp
#define macro(z, n, data) ...
BOOST_PP_REPEAT(5, macro, data)
```

���Υѥ�᡼���� `BOOST_PP_REPEAT` �ᥫ�˥���ؤ����˸�ΨŪ�ʺ��������ѤǤ��롣
�������ʤ��顢�饤�֥��ϼ�ưŪ�˼���ȿ�������򸫤Ĥ��뤿�ᡢ�����ɬ������Ȥ�ɬ�פϤʤ���

##�����ν���դ�

���������μ�ưŪ�ʸ��Τˤ�ꡢ`BOOST_PP_REPEAT_1ST`��`BOOST_PP_REPEAT_2ND`��`BOOST_PP_3RD`��������Ϥ���ƻȤ����Ȥϰ����Ǥʤ���
�����Υޥ���� *��ư�Ƶ�* �ᥫ�˥����Х��ѥ������ޤ� *��ư�Ƶ�* �ᥫ�˥����Ŭ�ڤʽ���ǥޥ����Ȥ��뤳�Ȥ˰�¸���Ƥ��롣
�����ΥХ��ѥ��ޥ����Ȥ��ʤ顢���ֳ�¦��ȿ���� `BOOST_PP_REPEAT_1ST`������ `BOOST_PP_REPEAT_2ND`���Ǹ夬 `BOOST_PP_REPEAT_3RD` �� *�ʤ���Фʤ�ʤ�*��
����ʳ��λȤ������ϥ饤�֥��ˤ�äƥ��ݡ��Ȥ���ʤ���
������ư��뤫�⤷��ʤ�����ư��ʤ����Ȥ⤢�뤫�⤷��ʤ���

##������ʸ

*��ư�Ƶ�* ��Ʊ�ͤ����꤬���롣
������ `BOOST_PP_WHILE` �κƵ���ʸ(��Ʊ�ͤ� `BOOST_PP_FOR`)�ϼ��Τ褦�Ǥ��ä�:

```cpp
BOOST_PP_WHILE ## d(pred, op, state)
```

...���뤤��:

```cpp
BOOST_PP_CAT(BOOST_PP_WHILE, d)(pred, op, state)
```

*��ư�Ƶ�* ��ǥ�ˤ����ơ�`BOOST_PP_CAT` �С������ϻȤ��ʤ���
�ʤ��ʤ� `BOOST_PP_CAT` ��Ϣ������˰�����Ÿ�����������`BOOST_PP_WHILE` �ϰ���̵����Ÿ�����뤫��Ǥ��롣
���Υ饤�֥��Ǥ����3�ĤΥѥ�᡼������褦�˸����뤬������������� *��ư�Ƶ�* �Υȥ�å��Ǥ��롣
����ϼ��Τ褦�ʤ�Τ�Ʊ�ͤǤ���:

```cpp
#define A(x, y) ...
#define B A
// ...
B(2, 3)
```

���ι�ʸ�� `B` �ޥ���2�Ĥΰ�����Ȥ�褦�˸����뤬���ºݤϤ����ǤϤʤ���
���� `B` �ޥ��� `A` �˿�ܤ��뤳�Ȥ�����Ƥϡ� *��ư�Ƶ�* �ᥫ�˥����Ʊ�ͤ�ή����ư��롣

�����Ĥ��Υץ�ץ��å���ư��٤����ᡢľ��Ū�ʺ���(*��ư�Ƶ�* ̵����)�������Ĥ��������ʥ������Ǥ��ޤ���ɬ�פȤ���롣
���η�̡��饤�֥��Ϻ����Τ���˿�������ʸ��Ȥ�:

```cpp
BOOST_PP_FOR_ ## r(state, pred, op, macro)
BOOST_PP_REPEAT_ ## z(count, macro, data)
BOOST_PP_WHILE_ ## d(pred, op, state)
```

##���߹���

������ `BOOST_PP_LIST_FOLD_RIGHT` �ޥ���ΰ����� `BOOST_PP_LIST_FOLD_LEFT` �εս�Ǥ��ä���
�ޤ���`BOOST_PP_LIST_FOLD_RIGHT` ���Ϥ���뽸�ѥޥ����դΰ����ǸƤФ�Ƥ�����
���ο����㤤�ϲ�ä��줿��

�㼨����ȡ�`BOOST_PP_LIST_FOLD_RIGHT` �ϼ��Τ褦�Ǥ��ä�:

```cpp
#define macro(d, elem, state)
BOOST_PP_LIST_FOLD_RIGHT(macro, list, state)
```

����ϼ��Τ褦���֤�����ä�...

```cpp
#define macro(d, state, elem)
BOOST_PP_LIST_FOLD_RIGHT(macro, state, list)
```

##����

���Υ饤�֥���1.28��꡼���ˤ�̵����������ǽ�򤿤�������äƤ��ơ����Υꥹ�ȤϤ�������Ƥ���󤹤��ΤǤϤʤ���
�����ñ�ˡ���������꡼���˸ߴ��Ȥʤ뤿��˥����ɤ��ѹ���������Фʤ�ʤ���ΤΥꥹ�ȤǤ��롣

##See Also

- [`BOOST_PP_FOR`](../ref/for.md)
- [`BOOST_PP_LIST_FOLD_RIGHT`](../ref/list_fold_right.md)
- [`BOOST_PP_REPEAT`](../ref/repeat.md)
- [`BOOST_PP_WHILE`](../ref/while.md)

---

Paul Mensonides

