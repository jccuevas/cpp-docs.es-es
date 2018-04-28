---
title: Compilador advertencia (nivel 1) C4052 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- C4055
dev_langs:
- C++
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29b1c8bcc836e35f7b8b81954ef247527d8ec35e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="compiler-warning-level-1-c4055"></a>Advertencia del compilador (nivel 1) C4055

> '*conversión*': del puntero de datos '*type1*'al puntero de función'*type2*'

## <a name="remarks"></a>Comentarios

**Obsoleto:** 2017 de Visual Studio y versiones posteriores no genera esta advertencia.

Un puntero de datos se convierte (quizás incorrectamente) en un puntero de función. Se trata de una advertencia de nivel 1 en /Za y una advertencia de nivel 4 en /Ze.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4055:

```C
// C4055.c
// compile with: /Za /W1 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
   return (PFUNC)pi;   // C4055
}
```

En /Ze, esta es una advertencia de nivel 4.

```C
// C4055b.c
// compile with: /W4 /c
typedef int (*PFUNC)();
int *pi;
PFUNC f() {
return (PFUNC)pi;   // C4055
}
```
