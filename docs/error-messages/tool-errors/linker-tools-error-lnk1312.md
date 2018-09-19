---
title: Las herramientas del vinculador LNK1312 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1312
dev_langs:
- C++
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 335a3976675f36e3da295bc23c8e17440a56a505
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088659"
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