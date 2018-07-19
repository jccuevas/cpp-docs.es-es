---
title: Error del compilador C2144 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2144
dev_langs:
- C++
helpviewer_keywords:
- C2144
ms.assetid: 49f3959b-324f-4c06-9588-c0ecef5dc5b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60a6b0a6019ab6ddf1a403d2cbd4f6ef96b2a865
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171157"
---
# <a name="compiler-error-c2144"></a>Error del compilador C2144

> error de sintaxis: '*tipo*'debe ir precedido de'*token*'

El compilador esperado *token* y encuentra *tipo* en su lugar.

Este error puede deberse a una falta llave de cierre, un paréntesis de cierre o un punto y coma.

También puede producirse el error C2144 al intentar crear una macro de una palabra clave CLR que contiene un carácter de espacio en blanco.

También puede ver error C2144 si está intentando reenvío de tipos. Vea [Type Forwarding (C++ / CLI)](../../windows/type-forwarding-cpp-cli.md) para obtener más información.

## <a name="examples"></a>Ejemplos

El ejemplo siguiente genera el error C2144 y muestra una forma de corregirlo:

```cpp
// C2144.cpp
// compile with: /clr /c
#define REF ref
REF struct MyStruct0;   // C2144

// OK
#define REF1 ref struct
REF1 MyStruct1;
```

El ejemplo siguiente genera el error C2144 y muestra una forma de corregirlo:

```cpp
// C2144_2.cpp
// compile with: /clr /c
ref struct X {

   property double MultiDimProp[,,] {   // C2144
   // try the following line instead
   // property double MultiDimProp[int , int, int] {
      double get(int, int, int) { return 1; }
      void set(int i, int j, int k, double l) {}
   }

   property double MultiDimProp2[] {   // C2144
   // try the following line instead
   // property double MultiDimProp2[int] {
      double get(int) { return 1; }
      void set(int i, double l) {}
   }
};
```