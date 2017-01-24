---
title: "Error del compilador C3706 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3706"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3706"
ms.assetid: d20a33eb-d625-46c5-ac87-32075a590d07
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3706
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : debe ser una interfaz COM para desencadenar eventos COM  
  
 La interfaz de eventos que se utiliza para desencadenar eventos COM debe ser una interfaz COM.  En esta situación, la interfaz debería definirse usando un atributo de Visual C\+\+ o importarse usando [\#import](../../preprocessor/hash-import-directive-cpp.md) de una biblioteca de tipos con el atributo embedded\_idl de \#import.  
  
 Observe que las líneas `#include` de los archivos de encabezado ATL que se muestran en el ejemplo de abajo son necesarias para utilizar eventos COM.  Para resolver este error, convierta `IEvents` \(la interfaz de eventos\) en interfaz COM aplicando uno de los siguientes atributos a la definición de interfaz: [object](../Topic/object%20\(C++\).md), [dual](../Topic/dual.md) o [dispinterface](../../windows/dispinterface.md).  
  
 Si una interfaz es de un archivo de encabezado generado por MIDL, el compilador no la reconocerá como una interfaz COM.  
  
 El código siguiente genera el error C3706:  
  
```  
// C3706.cpp  
// compile with: /c  
// C3706 expected  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(dll, name="idid", uuid="12341234-1234-1234-1234-123412341234")];  
  
// Uncomment the following line to resolve.  
// [object, uuid="12341234-1234-1234-1234-123412341237"]  
__interface IEvents : IUnknown {  
   HRESULT event1(/*[in]*/ int i);   // uncomment [in]  
};  
  
[dual, uuid="12341234-1234-1234-1234-123412341235"]  
__interface IBase {  
   HRESULT fireEvents();  
};  
  
[coclass, event_source(com), uuid="12341234-1234-1234-1234-123412341236"]  
class CEventSrc : public IBase {  
   public:  
   __event __interface IEvents;  
  
   HRESULT fireEvents() {  
      HRESULT hr = IEvents_event1(123);  
      return hr;  
   }  
};  
```