---
title: isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered
ms.date: 01/31/2019
f1_keywords:
- isgreater
- math/isgreater
- isgreaterequal
- math/isgreaterequal
- isless
- math/isless
- islessequal
- math/islessequal
- islessgreater
- math/islessgreater
- isunordered
- math/isunordered
helpviewer_keywords:
- isgreater function
- isgreaterequal function
- isless function
- islessequal function
- islessgreater function
- isunordered function
ms.openlocfilehash: 748360cae1dd0ee43645dee369c60c835246ed03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333708"
---
# <a name="isgreater-isgreaterequal-isless-islessequal-islessgreater-isunordered"></a>isgreater, isgreaterequal, isless, islessequal, islessgreater, isunordered

Determina la relación entre dos valores de punto flotante de ordenación.

## <a name="syntax"></a>Sintaxis

```C
int isgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isgreaterequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isless(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessequal(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int islessgreater(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */

int isunordered(
   /* floating-point */ x,
   /* floating-point */ y
); /* C-only macro */
```

```C++
template <class FloatingType1, class FloatingType2>
inline bool isgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isgreaterequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isless(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessequal(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool islessgreater(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */

template <class FloatingType1, class FloatingType2>
inline bool isunordered(
   FloatingType1 x,
   FloatingType2 y
) throw(); /* C++-only template function */
```

### <a name="parameters"></a>Parámetros

*x*, *y*<br/>
Valores de punto flotante que se va a comparar.

## <a name="return-value"></a>Valor devuelto

En todas las comparaciones, infinitos del mismo signo se consideran iguales. Infinito negativo es menor que cualquier valor finito o infinito positivo. Infinito positivo es mayor que cualquier valor finito o infinito negativo. Ceros son iguales independientemente de inicio de sesión. NaN no es menor, igual o mayor que cualquier valor, incluido otro NaN.

Cuando ningún argumento es NaN, las macros de ordenación **isgreater**, **isgreaterequal**, **isless**, y **islessequal** devolver distinto de cero el valor si la relación de ordenación especificada entre *x* y *y* es verdadero. Estas macros devuelven 0 si uno o ambos argumentos son NaN o si la relación de ordenación es false. Los formularios de función se comportan del mismo modo, pero devolver **true** o **false**.

El **islessgreater** macro devuelve un valor distinto de cero si ambos *x* y *y* no son NaN, y *x* sea menor o mayor que *y*. Devuelve 0 si uno o ambos argumentos son NaN, o si los valores son iguales. El formulario de la función se comporta del mismo modo, pero devuelve **true** o **false**.

El **isunordered** macro devuelve un valor distinto de cero si *x*, *y*, o ambos parámetros son valores NaN. De lo contrario, devuelve 0. El formulario de la función se comporta del mismo modo, pero devuelve **true** o **false**.

## <a name="remarks"></a>Comentarios

Estas operaciones de comparación se implementan como macros cuando se compila como C y como funciones de plantilla en línea cuando se compila como C++.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario (C)|Encabezado necesario (C++)|
|--------------|---------------------------|-------------------------------|
| **isgreater**, **isgreaterequal**, **isless**,<br/>**islessequal**, **islessgreater**, **isunordered** | \<math.h> | \<math.h> o \<cmath> |

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[isfinite, _finite y _finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[_fpclass, _fpclassf](fpclass-fpclassf.md)<br/>
