---
title: Advertencia del compilador (nivel 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4055
helpviewer_keywords:
- C4055
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: e9fcb4356d993d86b622fd49c4a75d587554f7c2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388610"
---
# <a name="compiler-warning-level-1-c4055"></a>Advertencia del compilador (nivel 1) C4055

> '*conversión*': del puntero de datos '*type1*'a puntero a función'*type2*'

## <a name="remarks"></a>Comentarios

**Obsoleto:** Esta advertencia no se genera mediante Visual Studio 2017 y versiones posteriores.

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
