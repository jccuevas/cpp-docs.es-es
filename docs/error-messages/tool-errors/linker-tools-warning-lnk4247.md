---
title: Advertencia de las herramientas del vinculador LNK4247
ms.date: 11/04/2016
f1_keywords:
- LNK4247
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
ms.openlocfilehash: 344c219fa1f3daa1e5f9c31431e608f5e7036400
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991157"
---
# <a name="linker-tools-warning-lnk4247"></a>Advertencia de las herramientas del vinculador LNK4247

el punto de entrada ' decorated_function_name ' ya tiene un atributo Thread; ' atributo ' omitido

Un punto de entrada, especificado con [/entry (símbolo de punto de entrada)](../../build/reference/entry-entry-point-symbol.md), tenía un atributo de subprocesos, pero también se especificó [/CLRTHREADATTRIBUTE (establecer el atributo de subproceso de CLR)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) , con un modelo de subprocesos diferente.

El enlazador omitió el valor especificado con/CLRTHREADATTRIBUTE.

Para resolver esta ADVERTENCIA:

- Quite/CLRTHREADATTRIBUTE de la compilación.

- Quite el atributo del archivo de código fuente.

- Quite el atributo del origen y/CLRTHREADATTRIBUTE de la compilación y acepte el modelo de subprocesos de CLR predeterminado.

- Cambie el valor pasado a/CLRTHREADATTRIBUTE, de modo que acepte el atributo de origen.

- Cambiar el atributo en el origen, de modo que acepte el valor pasado a/CLRTHREADATTRIBUTE.

En el ejemplo siguiente se genera LNK4247

```cpp
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```
