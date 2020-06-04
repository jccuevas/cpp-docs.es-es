---
title: cambiar nombre de atributo de importación
ms.date: 08/29/2019
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: 520369f0308078fead2947e27a512f25a3ad3fab
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447487"
---
# <a name="rename-import-attribute"></a>cambiar nombre de atributo de importación

**C++Cuestión**

Resuelve problemas del conflicto de nombres.

## <a name="syntax"></a>Sintaxis

> **#import** **cambiar el nombre** *de la biblioteca de tipos* ("*OldName*" **,** "*NewName*" **)**

### <a name="parameters"></a>Parámetros

\ *OldName*
Nombre anterior en la biblioteca de tipos.

*NewName*\
Nombre usado en lugar del nombre anterior.

## <a name="remarks"></a>Observaciones

Cuando se especifica el atributo **Rename** , el compilador reemplaza todas las apariciones de *OldName* en la *biblioteca de tipos* con el *NewName* proporcionado por el usuario en los archivos de encabezado resultantes.

Se puede usar el atributo **Rename** cuando un nombre de la biblioteca de tipos coincide con una definición de macro en los archivos de encabezado del sistema. Si no se resuelve esta situación, el compilador puede emitir varios errores de sintaxis, como el [error del compilador C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) y el [error del compilador C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> La sustitución se aplica a un nombre usado en la biblioteca de tipos, no a un nombre usado en el archivo de encabezado resultante.

Suponga, por ejemplo, que hay una propiedad denominada `MyParent` en una biblioteca de tipos y que se define una macro `GetMyParent` en un archivo de encabezado y se utiliza antes de `#import`. Puesto que `GetMyParent` es el nombre predeterminado de una función contenedora para la propiedad `get` de control de errores, se producirá un conflicto de nombres. Para solucionar el problema, utilice el siguiente atributo en la instrucción `#import`:

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

que cambia el nombre `MyParent` en la biblioteca de tipos. Un intento de cambiar el nombre del contenedor `GetMyParent` producirá un error:

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

Se debe a que el nombre `GetMyParent` solo se produce en el archivo de encabezado de la biblioteca de tipos resultante.

**Específico C++ de finalización**

## <a name="see-also"></a>Consulte también

[#import atributos](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
