---
title: Compilador advertencia (nivel 1) C4581 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4581
dev_langs:
- C++
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 415fb9ffc3e53ddfe9edcee2ec99361b38de0dea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4581"></a>Advertencia del compilador (nivel 1) C4581
comportamiento en desuso: '"cadena1" ' reemplazado por 'cadena2' para procesar el atributo  
  
 Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: comprobación de parámetros de atributos de Visual C++.  
  
 En versiones anteriores, los valores de atributo se aceptaron si o no se incluían entre comillas. Si el valor es una enumeración, no debe incluirse entre comillas.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4581.  
  
```  
// C4581.cpp  
// compile with: /c /W1  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {};  
  
[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581  
// try the following line instead  
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]  
class CSample : public IMyI {};  
```