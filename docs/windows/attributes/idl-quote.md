---
title: idl_quote (C++ atributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.idl_quote
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
ms.openlocfilehash: fd7455298c9a1b69926d85766b6cd7f96bd374cc
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59037122"
---
# <a name="idlquote"></a>idl_quote

Le permite usar construcciones IDL que no se admiten en la versión actual de Visual C++ y pídales que pasen al archivo .idl generado.

## <a name="syntax"></a>Sintaxis

```cpp
[ idl_quote(text) ]
```

### <a name="parameters"></a>Parámetros

*texto*<br/>
El nombre del atributo que desea que el compilador de Visual C++ que pasan a través del archivo .idl generado sin devolver un error del compilador.

## <a name="remarks"></a>Comentarios

Si el **idl_quote** C++ atributo se utiliza como un atributo independiente (con un punto y coma después del corchete de cierre), a continuación, *texto* se coloca en el archivo .idl combinados tal cual. Si **idl_quote** se utiliza en un símbolo, *texto* se coloca dentro del bloque de atributos para dicho símbolo.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo puede especificar un atributo no admitido (mediante **en**, que se admite) y cómo definir y usar una construcción de IDL no definido:

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

Este código provoca `MYFLOT` y `MYDUB` y *texto* entrada que se colocarán en el archivo .idl generado. El *nombre* parámetro fuerza *texto* colocarse antes de todo lo que hace referencia a *nombre* en el archivo .idl generado. El *dependencias* parámetro fuerza se coloca delante de las definiciones de lista dependencia *texto* en el archivo .idl generado.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Contexto de atributo

|||
|-|-|
|**Se aplica a**|En cualquier lugar|
|**Reiterativo**|No|
|**Atributos requeridos**|Ninguna|
|**Atributos no válidos**|Ninguna|

Para obtener más información, vea [Contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vea también

[Atributos IDL](idl-attributes.md)<br/>
[Atributos independientes](stand-alone-attributes.md)