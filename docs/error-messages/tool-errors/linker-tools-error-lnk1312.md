---
title: Error de las herramientas del vinculador LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: 49fa7e7963d6bb561e1602b58fe1f26c5f3d54bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436236"
---
# <a name="linker-tools-error-lnk1312"></a>Error de las herramientas del vinculador LNK1312

archivo no válido o dañado: no se puede importar el ensamblado

Al compilar un ensamblado, un archivo que no sea un módulo o un ensamblado compilado con **/CLR** se pasó a la **/ASSEMBLYMODULE** opción del vinculador.  Si pasa un archivo de objeto a **/ASSEMBLYMODULE**, simplemente pase el objeto directamente al vinculador, en lugar de a **/ASSEMBLYMODULE**.

## <a name="example"></a>Ejemplo

El ejemplo siguiente crea el archivo .obj.

```
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error LNK1312.

```
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```