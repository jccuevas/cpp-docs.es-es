---
title: Error del compilador C3345 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3345
dev_langs: C++
helpviewer_keywords: C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae9a2cc09dfed19874b8c1525e91732f702e6d75
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3345"></a>Error del compilador C3345
'identifier': identificador no válido para el nombre de módulo  
  
 El elemento *identifier* de un módulo contiene uno o más caracteres no aceptados. Un identificador es válido si el primer carácter es una letra, un carácter de subrayado o un carácter ANSI (0x80-FF) alto y cualquier carácter posterior es alfanumérico, un carácter de subrayado o un carácter ANSI alto.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Asegúrese de que el elemento *identifier* no contenga espacios en blanco u otros caracteres inaceptables.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente causa el mensaje de error C3345 porque el parámetro `name` del atributo `module` contiene un espacio en blanco.  
  
```  
// cpp_attr_name_module.cpp  
// compile with: /LD /link /OPT:NOREF  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
// C3345 expected  
[module(dll, name="My Library", version="1.2", helpfile="MyHelpFile")]   
// Try the following line instead  
//[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]   
// Module attribute now applies to this class  
class CMyClass {  
public:  
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {  
   // add your own code here  
   return __super::DllMain(dwReason, lpReserved);  
   }  
};  
```  
  
## <a name="see-also"></a>Vea también  
 [__iscsym](../../c-runtime-library/reference/iscsym-functions.md)   
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [módulo](../../windows/module-cpp.md)