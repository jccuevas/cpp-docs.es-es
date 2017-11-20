---
title: 'auto_handle:: ~ auto_handle | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- auto_handle.~auto_handle
- msclr.auto_handle.~auto_handle
- auto_handle::~auto_handle
- ~auto_handle
- msclr::auto_handle::~auto_handle
dev_langs: C++
helpviewer_keywords: auto_handle::~auto_handle
ms.assetid: e83e95a8-015b-4f27-ad63-70efb3690726
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 53f9f97044d2a8723723a586e48d252b1917ab02
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="autohandleautohandle"></a>auto_handle::~auto_handle
El `auto_handle` destructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
~auto_handle();  
```  
  
## <a name="remarks"></a>Comentarios  
 El destructor también destruye el objeto en propiedad.  
  
## <a name="example"></a>Ejemplo  
  
```  
// msl_auto_handle_dtor.cpp  
// compile with: /clr  
#include "msclr\auto_handle.h"  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
public:  
   ClassA() { Console::WriteLine( "ClassA constructor" ); }  
   ~ClassA() { Console::WriteLine( "ClassA destructor" ); }  
};  
  
int main()  
{  
   // create a new scope for a:  
   {  
      auto_handle<ClassA> a = gcnew ClassA;  
   }  
   // a goes out of scope here, invoking its destructor  
   // which in turns destructs the ClassA object.  
  
   Console::WriteLine( "done" );  
}  
```  
  
```Output  
ClassA constructor  
ClassA destructor  
done  
```  
  
## <a name="requirements"></a>Requisitos  
 **Archivo de encabezado** \<msclr\auto_handle.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Vea también  
 [auto_handle (miembros)](../dotnet/auto-handle-members.md)   
 [auto_handle::Release](../dotnet/auto-handle-release.md)   
 [auto_handle::auto_handle](../dotnet/auto-handle-auto-handle.md)