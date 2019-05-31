---
title: enable_if (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::enable_if
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
ms.openlocfilehash: 450664f71851778cc40160e55cbb80bcb51330d5
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66451258"
---
# <a name="enableif-class"></a>enable_if (Clase)

Realiza una instancia de manera condicional de un tipo para la resolución de sobrecarga SFINAE. El objeto typedef anidado `enable_if<Condition,Type>::type` existe, y es un sinónimo de `Type`, si y solo si `Condition` es **true**.

## <a name="syntax"></a>Sintaxis

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>Parámetros

*B*<br/>
El valor que determina la existencia del tipo resultante.

*T*<br/>
El tipo para crear una instancia si *B* es true.

## <a name="remarks"></a>Comentarios

Si *B* es true, `enable_if<B, T>` tiene una definición de tipo anidada llamada "tipo" que es un sinónimo de *T*.

Si *B* es false, `enable_if<B, T>` no tiene una definición de tipo anidada llamada "tipo".

Se proporciona esta plantilla de alias:

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

En C++, el error en la sustitución de parámetros de la plantilla no es un error en sí mismo, esto se denomina *SFINAE* (el error en la sustitución no es un error). Normalmente, `enable_if` se utiliza para eliminar candidatos de la resolución de sobrecarga, es decir, selecciona los conjuntos de sobrecarga para que una definición se pueda rechazar en favor de otra. Esto se ajusta al comportamiento SFINAE. Para obtener más información sobre SFINAE, vea el artículo de la Wikipedia sobre [el error en la sustitución no es un error](https://go.microsoft.com/fwlink/p/?linkid=394798).

A continuación, se presentan cuatro escenarios de ejemplo:

- Escenario 1: Ajustar el valor devuelto de una función:

```cpp
    template <your_stuff>
typename enable_if<your_condition, your_return_type>::type
    yourfunction(args) {// ...
}
// The alias template makes it more concise:
    template <your_stuff>
enable_if_t<your_condition, your_return_type>
yourfunction(args) {// ...
}
```

- Escenario 2: Añadir un parámetro de función que tiene un argumento predeterminado:

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
}
```

- Escenario 3: Añadir un parámetro de plantilla que tiene un argumento predeterminado:

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- Escenario 4: Si su función tiene un argumento sin plantilla, puede ajustar su tipo:

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
}
```

El escenario 1 no funciona con constructores y operadores de conversión porque no tienen tipos de retorno.

El escenario 2 deja el parámetro sin nombre. Podría decir `::type Dummy = BAR`, pero el nombre `Dummy` es irrelevante y si se le da un nombre es probable que desencadene una advertencia "parámetro sin referencia". Debe elegir un tipo de parámetro de función `FOO` y un argumento predeterminado `BAR`.  Podría decir **int** y `0`, pero, a continuación, los usuarios de su código podrían pasar por error a la función entero adicional que se ignorarán. En su lugar, se recomienda que use `void **` y `0` o **nullptr** porque casi nada se puede convertir a `void **`:

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

El escenario 2 también funciona para constructores ordinarios.  Sin embargo, no funciona para operadores de conversión, porque no pueden tomar parámetros adicionales.  Tampoco funciona para constructores [variadic](../cpp/ellipses-and-variadic-templates.md), porque agregar parámetros adicionales convierte el paquete de parámetros de funciones en un contexto no deducido y, de este modo, rechaza el objetivo de `enable_if`.

El escenario 3 utiliza el nombre `Dummy`, pero es opcional. Simplemente "`typename = typename`" podría funcionar, pero, si cree que parece raro, puede usar un nombre ficticio, solo asegúrese de no usar uno que también pueda emplearse en la definición de la función. Si no da un tipo a `enable_if`, se anula de manera predeterminada y esto es perfectamente razonable porque a usted le da igual qué es `Dummy`. Esto funciona para todo, incluidos los operadores de conversión y los constructores [variadic](../cpp/ellipses-and-variadic-templates.md).

El escenario 4 funciona en constructores que no tienen tipos de valor devueltos y, de este modo, soluciona la limitación del ajuste del escenario 1.  Sin embargo, el escenario 4 se limita a argumentos de función sin plantilla, que no siempre están disponibles.  (Utilizar el escenario 4 en un argumento de función con plantilla evita que la deducción de argumentos de plantilla funcione en él.)

`enable_if` es eficaz, pero también peligroso si se utiliza incorrectamente.  Como su objetivo es hacer desaparecer a los candidatos antes de la resolución de sobrecarga, si se utiliza incorrectamente, sus efectos pueden ser muy confusos.  A continuación se muestran algunas recomendaciones:

- No utilice `enable_if` para seleccionar entre implementaciones en tiempo de compilación. No escriba nunca un `enable_if` para `CONDITION` y otro para `!CONDITION`.  En lugar de eso, use un patrón de *envío de etiquetas*, por ejemplo, un algoritmo que seleccione implementaciones en función de las ventajas de los iteradores que se les han otorgado.

- No utilice `enable_if` para exigir requisitos.  Si quiere validar los parámetros de la plantilla, y si se produce un error en la validación, provoque un error en lugar de seleccionar otra implementación, use [static_assert](../cpp/static-assert.md).

- Utilice `enable_if` cuando tenga un conjunto de sobrecarga que convierta en ambiguos ciertos códigos que en otras circunstancias serían buenos.  Frecuentemente, esto sucede en constructores que convierten implícitamente.

## <a name="example"></a>Ejemplo

Este ejemplo explica cómo la función de plantilla de biblioteca estándar de C++ [std::make_pair()](../standard-library/utility-functions.md#make_pair) se aprovecha de `enable_if`.

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

En este ejemplo, `make_pair("foo", "bar")` devuelve `pair<const char *, const char *>`. La resolución de sobrecarga debe determinar qué `func()` quiere. `pair<A, B>` tiene un constructor que convierte implícitamente de `pair<X, Y>`.  Esto no es nuevo, ya sucedía en C++98. No obstante, en C++98/03, la firma del constructor que convierte implícitamente existe siempre, incluso si es `pair<int, int>(const pair<const char *, const char *>&)`.  La resolución de sobrecarga no le importa que un intento de crear una instancia de ese constructor explote horriblemente, porque `const char *` no es implícitamente convertible a **int**; solo se examina firmas, antes de la función son definiciones crea una instancia.  Por lo tanto, el código de ejemplo es ambiguo, porque las firmas existen para convertir `pair<const char *, const char *>` tanto a `pair<int, int>` y a `pair<string, string>`.

C++11 ha solucionado esta ambigüedad usando `enable_if` para asegurarse de que `pair<A, B>(const pair<X, Y>&)` existiera **solo** cuando `const X&` pueda convertirse implícitamente en `A` y `const Y&` pueda convertirse implícitamente en `B`.  Esto permite que la resolución de sobrecarga determine que `pair<const char *, const char *>` no se puede convertir en `pair<int, int>` y que la sobrecarga que toma `pair<string, string>` es viable.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
