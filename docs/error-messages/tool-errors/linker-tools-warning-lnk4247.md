---
title: Las herramientas del vinculador LNK4247 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4247
dev_langs:
- C++
helpviewer_keywords:
- LNK4247
ms.assetid: 085d7fdf-9eaf-4641-8473-6eaadd073c7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d84a5964cb8df5d2973b6031da55d48dade584e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078015"
---
# <a name="linker-tools-warning-lnk4247"></a>Advertencia de las herramientas del vinculador LNK4247

punto de entrada 'nombre_representativo_de_función' ya tiene un atributo de subproceso; 'atributo' omitido

Un punto de entrada con [/Entry (símbolo de punto de entrada)](../../build/reference/entry-entry-point-symbol.md), tenía un atributo de subprocesamiento, pero [/CLRTHREADATTRIBUTE (Establecer atributo de subproceso de CLR)](../../build/reference/clrthreadattribute-set-clr-thread-attribute.md) también se especificó con un modelo de subprocesos diferentes.

El vinculador omitió el valor especificado con/CLRTHREADATTRIBUTE.

Para resolver esta advertencia:

- Quitar/CLRTHREADATTRIBUTE de la compilación.

- Quite el atributo de archivo de código fuente.

- Elimine el atributo de origen y/CLRTHREADATTRIBUTE desde la compilación y acepte el modelo de subprocesos de CLR de forma predeterminada.

- Cambie el valor pasado a/CLRTHREADATTRIBUTE, que lo está de acuerdo con el atributo de origen.

- Cambie el atributo de origen, de modo que lo está de acuerdo con el valor pasado a/CLRTHREADATTRIBUTE.

El ejemplo siguiente genera la advertencia LNK4247

```
// LNK4247.cpp
// compile with: /clr /c
// post-build command: link /CLRTHREADATTRIBUTE:STA LNK4247.obj /entry:functionTitle /SUBSYSTEM:Console
[System::MTAThreadAttribute]
void functionTitle (){}
```