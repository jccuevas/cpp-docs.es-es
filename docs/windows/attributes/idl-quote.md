---
title: idl_quote (C++ atributo com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: 4b05da6d237d71e0cc645ad0f626f75ecd85c827
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168034"
---
# <a name="idl_quote"></a>idl_quote

Permite usar construcciones IDL que no se admiten en la versión actual de Visual C++ y hacer que pasen al archivo. idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>Parámetros

*text*<br/>
Nombre del atributo que desea que el compilador de Microsoft C++ pase por el archivo. idl generado sin devolver un error del compilador.

## <a name="remarks"></a>Observaciones

Si el atributo **idl_quote** C++ se utiliza como un atributo independiente (con un punto y coma después del corchete de cierre), el *texto* se coloca en el archivo. idl combinado tal y como está. Si se utiliza **idl_quote** en un símbolo, el *texto* se coloca dentro del bloque de atributos de dicho símbolo.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo se puede especificar un atributo no admitido (mediante **en**, que se admite) y cómo definir y usar una construcción. idl sin definir:

```cpp
// cpp_attr_ref_idl_quote.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLibrary")];

[export]
struct MYFLOT {
   int i;
};

[export]
struct MYDUB {
   int i;
};

[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];

typedef struct _S1_TYPE {
   long l1;

union {
   MYFLOT f1; MYDUB d2; } U1_TYPE;
} S1_TYPE;

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]
__interface IStatic{
   HRESULT Func1([idl_quote("in")] int i);
   HRESULT func( S1_TYPE* myStruct );
};
```

Este código hace que `MYFLOT` y `MYDUB` y la entrada de *texto* se coloquen en el archivo. idl generado. El parámetro *Name* fuerza el *texto* a colocarse delante de cualquier elemento que haga referencia al *nombre* en el archivo. idl generado. El parámetro *dependencies* obliga a que se coloquen las definiciones de lista de dependencias delante del *texto* del archivo. idl generado.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|None|
|**Atributos no válidos**|None|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)
