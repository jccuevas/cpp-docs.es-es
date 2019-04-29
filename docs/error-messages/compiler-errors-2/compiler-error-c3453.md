---
title: Error del compilador C3453
ms.date: 11/04/2016
f1_keywords:
- C3453
helpviewer_keywords:
- C3453
ms.assetid: dbefdbcf-f697-4239-b7a5-1d99b85e9e7f
ms.openlocfilehash: 2b3288d02c611bf6785ca1ea7757e2283d889050
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328642"
---
# <a name="compiler-error-c3453"></a>Error del compilador C3453

'attribute': atributo no aplicado porque el calificador 'assembly' no coincidía

Los atributos de ensamblado o de nivel de módulo pueden especificarse como instrucciones independientes.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3453.

```
// C3453.cpp
// compile with: /clr /c
[assembly:System::CLSCompliant(true)]   // C3453
// try the following line instead
// [assembly:System::CLSCompliant(true)];
ref class X {};
```