---
title: Lock::operator == | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- lock::operator==
- msclr.lock.operator==
- msclr::lock::operator==
- lock.operator==
dev_langs: C++
helpviewer_keywords: lock::operator==
ms.assetid: 3dcf1e5a-53fc-495d-9df5-d7849a41c36c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 33e372deb0bbae86efdf1a7c928d45e673e0b334
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="lockoperator"></a>lock::operator==
Operador de igualdad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<class T> bool operator==(  
   T t  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `t`  
 El objeto para comparar la igualdad.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `true` si `t` es el mismo que el objeto del bloqueo, `false` en caso contrario.  
  
## <a name="example"></a>Ejemplo  
  
```  
// msl_lock_op_eq.cpp  
// compile with: /clr  
#include <msclr/lock.h>  
  
using namespace System;  
using namespace System::Threading;  
using namespace msclr;  
  
int main () {  
   Object^ o1 = gcnew Object;  
   lock l1(o1);  
   if (l1 == o1) {  
      Console::WriteLine("Equal!");  
   }  
}  
```  
  
```Output  
Equal!  
```  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Vea también  
 [lock (miembros)](../dotnet/lock-members.md)   
 [lock::operator!=](../dotnet/lock-operator-inequality.md)