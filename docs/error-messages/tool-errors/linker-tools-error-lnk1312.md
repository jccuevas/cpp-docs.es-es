---
title: Error de las herramientas del vinculador LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: e462d24f2eb54718ba73617146aab96bb14a66df
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990910"
---
# <a name="linker-tools-error-lnk1312"></a>Error de las herramientas del vinculador LNK1312

archivo no válido o dañado: no se puede importar el ensamblado

Al compilar un ensamblado, se pasó a la opción del vinculador **/assemblymodule** un archivo que no sea un módulo o un ensamblado compilado con **/CLR** .  Si pasó un archivo objeto a **/assemblymodule**, simplemente pase el objeto directamente al enlazador, en lugar de a **/assemblymodule**.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se crea el archivo. obj.

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera LNK1312.

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
