---
title: C++Referencia del comprobador de directrices básicas
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
ms.openlocfilehash: 3fe8f1795416bd05ce2c8cc622664a3ff1d6c749
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467236"
---
# <a name="c-core-guidelines-checker-reference"></a>C++Referencia del comprobador de directrices básicas

Esta sección enumeran las advertencias del Comprobador de C++ Core Guidelines. Para obtener información sobre el análisis de código, vea [/Analyze (análisis de código)](/cpp/build/reference/analyze-code-analysis) y [Inicio rápido: análisisC++de código para C/](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Algunas advertencias que pertenecen a más de un grupo, y no todas las advertencias tienen un tema de referencia completa.

## <a name="owner_pointer-group"></a>Grupo OWNER_POINTER

[DONT_HEAP_ALLOCATE_MOVABLE_RESULT C26402](C26402.md)\
Devuelve un objeto con ámbito en lugar de un montón asignado si tiene un constructor de movimiento. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[RESET_OR_DELETE_OWNER C26403](C26403.md)\
Restablece o elimina explícitamente un propietario\<T > puntero '*variable*'. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[DONT_DELETE_INVALID C26404](C26404.md)\
No elimine un propietario\<T > que pueda estar en un estado no válido. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[DONT_ASSIGN_TO_VALID C26405](C26405.md)\
No asigne a un propietario\<T > que pueda estar en un estado válido. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[DONT_ASSIGN_RAW_TO_OWNER C26406](C26406.md)\
No asigne un puntero sin formato a un propietario\<T >. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[DONT_HEAP_ALLOCATE_UNNECESSARILY C26407](C26407.md)\
Prefiere objetos de ámbito, no asignar montones innecesariamente. Consulte [ C++ directrices básicas R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[USE_NOTNULL C26429](C26429.md)\
El símbolo '*Symbol*' no se ha probado nunca para obtener valores NULL, se puede marcar como not_null. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[TEST_ON_ALL_PATHS C26430](C26430.md)\
No se ha comprobado la nulidad del símbolo '*Symbol*' en todas las rutas de acceso. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[DONT_TEST_NOTNULL C26431](C26431.md)\
El tipo de expresión '*expr*' ya es GSL:: not_null. No se debe probar valores NULL. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>Grupo RAW_POINTER

[NO_RAW_POINTER_ASSIGNMENT C26400](c26400.md)\
No asigne el resultado de una llamada de función o asignación con un propietario\<T > valor devuelto a un puntero sin formato; en su lugar, utilice Owner\<T >. Consulte [ C++ las directrices básicas I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[DONT_DELETE_NON_OWNER C26401](c26401.md)\
No elimine un puntero sin formato que no sea propietario\<T >. Consulte [ C++ las directrices básicas I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[DONT_HEAP_ALLOCATE_MOVABLE_RESULT C26402](C26402.md)\
Devuelve un objeto con ámbito en lugar de un montón asignado si tiene un constructor de movimiento. Consulte [ C++ Core Guidelines R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[NO_MALLOC_FREE C26408](C26408.md)\
Evite malloc () y Free (), prefiere la versión nothrow de New con DELETE. Consulte [ C++ directrices básicas R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[NO_NEW_DELETE C26409](C26409.md)\
Evite llamar a New y DELETE explícitamente. Use STD:: make_unique\<T > en su lugar. Consulte [ C++ Core Guidelines R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[USE_NOTNULL C26429](C26429.md)\
El símbolo '*Symbol*' no se ha probado nunca para obtener valores NULL, se puede marcar como not_null. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[TEST_ON_ALL_PATHS C26430](C26430.md)\
No se ha comprobado la nulidad del símbolo '*Symbol*' en todas las rutas de acceso. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[DONT_TEST_NOTNULL C26431](C26431.md)\
El tipo de expresión '*expr*' ya es GSL:: not_null. No se debe probar valores NULL. Consulte [ C++ las directrices básicas F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[NO_POINTER_ARITHMETIC C26481](C26481.md)\
No usar aritmética de puntero. Use el intervalo en su lugar. Consulte [ C++ los límites de Core Guidelines. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[NO_ARRAY_TO_POINTER_DECAY C26485](C26485.md)\
Expresión '*expr*': no hay ninguna matriz para decadencia del puntero. Vea [ C++ los límites de Core Guidelines. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>Grupo UNIQUE_POINTER

[NO_REF_TO_CONST_UNIQUE_PTR C26410](C26410.md)\
El parámetro '*Parameter*' es una referencia a `const` puntero único, use const t * o const t & en su lugar. Consulte [ C++ directrices básicas R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[NO_REF_TO_UNIQUE_PTR C26411](C26411.md)\
El parámetro '*Parameter*' es una referencia a un puntero único y nunca se reasigna o se restablece. Use t * o t & en su lugar. Consulte [ C++ directrices básicas R. 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[RESET_LOCAL_SMART_PTR C26414](C26414.md)\
Mueve, copia, reasigna o restablece un puntero inteligente local "*Symbol*". Consulte [ C++ directrices básicas R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[SMART_PTR_NOT_NEEDED C26415](C26415.md)\
El parámetro de puntero inteligente '*Symbol*' solo se usa para tener acceso a un puntero incluido. Use T * o T & en su lugar. Consulte [ C++ Core Guidelines R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>Grupo SHARED_POINTER

[RESET_LOCAL_SMART_PTR C26414](C26414.md)\
Mueve, copia, reasigna o restablece un puntero inteligente local "*Symbol*". Consulte [ C++ directrices básicas R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[SMART_PTR_NOT_NEEDED C26415](C26415.md)\
El parámetro de puntero inteligente '*Symbol*' solo se usa para tener acceso a un puntero incluido. Use T * o T & en su lugar. Consulte [ C++ Core Guidelines R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[NO_RVALUE_REF_SHARED_PTR C26416](C26416.md)\
La referencia rvalue pasa el parámetro de puntero compartido '*Symbol*'. Pasar por valor en su lugar. Consulte [ C++ Core Guidelines R. 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[NO_LVALUE_REF_SHARED_PTR C26417](C26417.md)\
El parámetro de puntero compartido '*Symbol*' se pasa por referencia y no se restablece o se vuelve a asignar. Use T * o T & en su lugar. Consulte [ C++ directrices básicas R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[NO_VALUE_OR_CONST_REF_SHARED_PTR C26418](C26418.md)\
El parámetro de puntero compartido '*Symbol*' no se copia ni se mueve. Use T * o T & en su lugar. Consulte [ C++ directrices básicas R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>DECLARACIÓN de grupo

[NO_GLOBAL_INIT_CALLS C26426](C26426.md)\
El inicializador global llama a una función no constexpr '*Symbol*'. Consulte [ C++ las directrices básicas I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[NO_GLOBAL_INIT_EXTERNS C26427](C26427.md)\
El inicializador global tiene acceso al objeto extern '*Symbol*'. Consulte [ C++ las directrices básicas I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[NO_UNNAMED_RAII_OBJECTS C26444](c26444.md)\
Evite objetos sin nombre con construcción y destrucción personalizadas. Vea [es. 84: no (intentar) declarar una variable local sin nombre](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>CLASE de grupo

[DEFINE_OR_DELETE_SPECIAL_OPS C26432](C26432.md)\
Si define o elimina cualquier operación predeterminada en el tipo '*Symbol*', defina o elimine todas. Consulte [ C++ las directrices básicas C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[OVERRIDE_EXPLICITLY C26433](c26433.md)\
La función '*Symbol*' debe marcarse con ' override '. Vea [C. 128: las funciones virtuales deben especificar exactamente una de virtual, override o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[DONT_HIDE_METHODS C26434](C26434.md)\
La función '*symbol_1*' oculta una función no virtual '*symbol_2*'. Consulte [ C++ las directrices básicas C. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[SINGLE_VIRTUAL_SPECIFICATION C26435](c26435.md)\
La función ' Symbol ' debe especificar exactamente uno de los*símbolos*' virtual ', ' override ' o ' final '. Vea [C. 128: las funciones virtuales deben especificar exactamente una de virtual, override o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

[NEED_VIRTUAL_DTOR C26436](C26436.md)\
El tipo '*Symbol*' con una función virtual necesita un destructor público virtual o no virtual protegido. Consulte [ C++ las directrices básicas C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[NO_EXPLICIT_DTOR_OVERRIDE C26443](c26443.md)\
El destructor de invalidación no debe utilizar especificadores explícitos ' override ' o ' virtual '. Vea [C. 128: las funciones virtuales deben especificar exactamente una de virtual, override o final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="style-group"></a>ESTILO de grupo

[NO_GOTO C26438](C26438.md)\
Evite los `goto`. Consulte [ C++ directrices básicas es. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Grupo de funciones

[SPECIAL_NOEXCEPT C26439](C26439.md)\
Este tipo de función no puede iniciarse. Declárelo `noexcept`. Consulte [ C++ las directrices básicas F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[DECLARE_NOEXCEPT C26440](C26440.md)\
La función '*Symbol*' puede declararse `noexcept`. Consulte [ C++ las directrices básicas F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[DONT_THROW_IN_NOEXCEPT C26447](c26447.md)\
La función se declara **noexception** , pero llama a una función que puede producir excepciones.
Consulte [ C++ las directrices básicas: F. 6: si es posible que la función no se inicie, declárela noexception](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Grupo de SIMULTANEIDAD

[NO_UNNAMED_GUARDS C26441](C26441.md)\
Los objetos Guard deben tener nombre. Consulte [ C++ Core Guidelines CP. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Grupo CONST

[USE_CONST_REFERENCE_ARGUMENTS C26460](c26460.md)\
El argumento de referencia '*argument*' de la función '*function*' se puede marcar como `const`. Consulte [ C++ directrices básicas con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[USE_CONST_POINTER_ARGUMENTS C26461](c26461.md): \
El argumento de puntero '*argument*' de la función '*function*' se puede marcar como puntero a `const`. Consulte [ C++ directrices básicas con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[USE_CONST_POINTER_FOR_VARIABLE C26462](c26462.md)\
El valor al que apunta '*variable*' se asigna solo una vez, márquelo como puntero a `const`. Consulte [ C++ directrices básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[USE_CONST_FOR_ELEMENTS C26463](c26463.md)\
Los elementos de la matriz '*array*' se asignan solo una vez, Mark elements `const`. Consulte [ C++ directrices básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[USE_CONST_POINTER_FOR_ELEMENTS C26464](c26464.md)\
Los valores a los que apuntan los elementos de la matriz '*array*' solo se asignan una vez, marque los elementos como puntero en `const`. Consulte [ C++ directrices básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[USE_CONST_FOR_VARIABLE C26496](c26496.md)\
La variable '*variable*' se asigna solo una vez, márquela como `const`. Consulte [ C++ directrices básicas con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[USE_CONSTEXPR_FOR_FUNCTION C26497](c26497.md)\
Esta *función* de función puede marcarse como `constexpr` si se desea una evaluación en tiempo de compilación. Consulte [ C++ las directrices básicas F. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[USE_CONSTEXPR_FOR_FUNCTIONCALL C26498](c26498.md)\
Esta *función* de llamada de función puede utilizar `constexpr` si se desea la evaluación en tiempo de compilación. Consulte [ C++ directrices básicas con. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>TIPO de grupo

[DONT_SLICE C26437](C26437.md)\
No segmentar. Consulte [ C++ directrices básicas es. 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

[NO_CONST_CAST_UNNECESSARY C26465](c26465.md)\
No utilice `const_cast` para desechar `const`. `const_cast` no es necesario; Esta conversión no está quitando la constante o la volatilidad. Consulte [ C++ las instrucciones básicas Type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[NO_STATIC_DOWNCAST_POLYMORPHIC C26466](c26466.md)\
No use `static_cast` downcasts. Una conversión de un tipo polimórfico debe usar dynamic_cast. Consulte [ C++ las instrucciones básicas Type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[NO_REINTERPRET_CAST_FROM_VOID_PTR C26471](c26471.md)\
No utilice `reinterpret_cast`. Una conversión de void * puede usar `static_cast`. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[NO_CASTS_FOR_ARITHMETIC_CONVERSION C26472](C26472.md)\
No use un `static_cast` para las conversiones aritméticas. Use la inicialización de llave, GSL:: narrow_cast o GSL:: Narrow. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[NO_IDENTITY_CAST C26473](C26473.md)\
No convierta entre tipos de puntero en los que el tipo de origen y el tipo de destino sean los mismos. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[NO_IMPLICIT_CAST C26474](C26474.md)\
No convierta entre tipos de puntero cuando la conversión podría ser implícita. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[NO_FUNCTION_STYLE_CASTS C26475](C26475.md)\
No use conversiones de estilo de función. Consulte [ C++ directrices básicas es. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[NO_REINTERPRET_CAST C26490](c26490.md)\
No utilice `reinterpret_cast`. Consulte [ C++ las instrucciones básicas Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[NO_STATIC_DOWNCAST C26491](c26490.md)\
No use `static_cast` downcasts. Consulte [ C++ las instrucciones básicas Type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[NO_CONST_CAST C26492](c26492.md)\
No utilice `const_cast` para desechar `const`. Consulte [ C++ las instrucciones básicas Type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[NO_CSTYLE_CAST C26493](c26493.md)\
No use conversiones de estilo C. Consulte [ C++ las instrucciones básicas tipo. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[VAR_USE_BEFORE_INIT C26494](c26494.md)\
La variable '*variable*' no está inicializada. Siempre debe inicializarse un objeto. Consulte [ C++ instrucciones básicas Type. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[MEMBER_UNINIT C26495](c26495.md)\
La variable '*variable*' no está inicializada. Siempre debe inicializarse una variable de miembro. Consulte [ C++ las instrucciones básicas Type. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Grupo de límites

[USE_GSL_AT C26446](c26446.md)\
Prefiere usar `gsl::at()` en lugar de un operador de subíndice sin comprobar. Consulte [ C++ directrices básicas: Bounds. 4: no usar funciones y tipos de la biblioteca estándar que no estén comprobados](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[NO_POINTER_ARITHMETIC C26481](C26481.md)\
No usar aritmética de puntero. Use el intervalo en su lugar. Consulte [ C++ límites de directrices básicas. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[NO_DYNAMIC_ARRAY_INDEXING C26482](c26482.md)\
Solo se indexa en matrices mediante expresiones constantes. Consulte [ C++ límites de las directrices básicas. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[STATIC_INDEX_OUT_OF_RANGE C26483](c26483.md)\
El *valor* del valor está fuera de los límites (0, *enlazado*) de la variable '*variable*'. Solo el índice de las matrices usa expresiones constantes en los límites de la matriz. Consulte [ C++ límites de las directrices básicas. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[NO_ARRAY_TO_POINTER_DECAY C26485](C26485.md)\
Expresión '*expr*': no hay ninguna matriz para decadencia del puntero. Consulte los límites de las [ C++ directrices básicas. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Grupo de GSL

[NO_SPAN_REF C26445](c26445.md)\
Una referencia a `gsl::span` o `std::string_view` puede ser una indicación de un problema de duración.
Consulte [ C++ directrices básicas GSL. View: vistas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[USE_GSL_AT C26446](c26446.md)\
Prefiere usar `gsl::at()` en lugar de un operador de subíndice sin comprobar. Consulte [ C++ directrices básicas: Bounds. 4: no usar funciones y tipos de la biblioteca estándar que no estén comprobados](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[USE_GSL_FINALLY C26448](c26448.md)\
Considere la posibilidad de usar `gsl::finally` si la acción final está prevista. Consulte [ C++ directrices básicas: GSL. util: Utilities](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[NO_SPAN_FROM_TEMPORARY C26449](c26449.md)\
`gsl::span` o `std::string_view` creados a partir de un temporal no serán válidos cuando se invalide el temporal. Consulte [ C++ directrices básicas: GSL. View: vistas](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).

## <a name="deprecated-warnings"></a>Advertencias en desuso

Las siguientes advertencias están presentes en un conjunto de reglas experimental temprana del corrector instrucciones de núcleo, pero están en desuso y pueden omitirse. Las advertencias se sustituyen por advertencias de la lista anterior.

- DEREF_INVALID_POINTER 26412
- DEREF_NULLPTR 26413
- ASSIGN_NONOWNER_TO_EXPLICIT_OWNER 26420
- ASSIGN_VALID_OWNER 26421
- VALID_OWNER_LEAVING_SCOPE 26422
- ALLOCATION_NOT_ASSIGNED_TO_OWNER 26423
- VALID_ALLOCATION_LEAVING_SCOPE 26424
- ASSIGNING_TO_STATIC 26425
- NO_LIFETIME_TRACKING 26499

## <a name="see-also"></a>Consulte también

[Uso de C++ los comprobadores de directrices principales](using-the-cpp-core-guidelines-checkers.md)
