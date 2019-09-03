---
title: make_public (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.make_public
- make_public_CPP
helpviewer_keywords:
- pragmas, make_public
- make_public pragma
ms.assetid: c3665f4d-268a-4932-9661-c37c8ae6a341
ms.openlocfilehash: d12fab685e0088993cb43073c3603bda12edd2f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218819"
---
# <a name="make_public-pragma"></a>make_public (Pragma)

Indica que un tipo nativo debe tener accesibilidad pública de ensamblado.

## <a name="syntax"></a>Sintaxis

> **#pragma make_public (** *tipo* **)**

### <a name="parameters"></a>Parámetros

*type*\
Nombre del tipo que desea tener accesibilidad pública de ensamblado.

## <a name="remarks"></a>Comentarios

**make_public** es útil cuando el tipo nativo al que se desea hacer referencia es de un archivo de encabezado que no se puede cambiar. Si desea utilizar el tipo nativo en la firma de una función pública en un tipo con visibilidad de ensamblado pública, el tipo nativo también debe tener accesibilidad pública de ensamblado o el compilador emitirá una advertencia.

**make_public** debe especificarse en el ámbito global. Solo tiene efecto desde el punto en el que se declara hasta el final del archivo de código fuente.

El tipo nativo puede ser implícita o explícitamente privado. Para obtener más información, vea [visibilidad de tipos](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility).

## <a name="examples"></a>Ejemplos

El ejemplo siguiente es el contenido de un archivo de encabezado que contiene las definiciones de dos estructuras nativas.

```cpp
// make_public_pragma.h
struct Native_Struct_1 { int i; };
struct Native_Struct_2 { int i; };
```

En el ejemplo de código siguiente se usa el archivo de encabezado. Muestra que, a menos que marque explícitamente las estructuras nativas como públicas mediante **make_public**, el compilador generará una advertencia al intentar usar las estructuras nativas en la signatura de la función pública en un tipo administrado público.

```cpp
// make_public_pragma.cpp
// compile with: /c /clr /W1
#pragma warning (default : 4692)
#include "make_public_pragma.h"
#pragma make_public(Native_Struct_1)

public ref struct A {
   void Test(Native_Struct_1 u) {u.i = 0;}   // OK
   void Test(Native_Struct_2 u) {u.i = 0;}   // C4692
};
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
