---
title: "ConvertBSTRToString | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ConvertBSTRToString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConvertBSTRToString (función)"
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ConvertBSTRToString
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Convierte un valor `BSTR` en un **char \***.  
  
## Sintaxis  
  
```  
  
      char* __stdcall ConvertBSTRToString(  
   BSTR pSrc  
);  
```  
  
#### Parámetros  
 `pSrc`  
 Una variable BSTR.  
  
## Comentarios  
 `ConvertBSTRToString` asigna una cadena que debe eliminar.  
  
## Ejemplo  
  
```  
// ConvertBSTRToString.cpp  
#include <comutil.h>  
#include <stdio.h>  
  
#pragma comment(lib, "comsuppw.lib")  
  
int main() {  
   BSTR bstrText = ::SysAllocString(L"Test");  
   wprintf_s(L"BSTR text: %s\n", bstrText);  
  
   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);  
   printf_s("char * text: %s\n", lpszText2);  
  
   SysFreeString(bstrText);  
   delete[] lpszText2;  
}  
```  
  
  **BSTR text: Test**  
**char \* text: Test**   
## FIN de Específicos de Microsoft  
  
## Requisitos  
 **Encabezado:** comutil.h.  
  
 **Lib:** omsuppw.lib o comsuppwd.lib \(vea [\/Zc:wchar\_t \(wchar\_t es un tipo nativo\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información\)  
  
## Vea también  
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)