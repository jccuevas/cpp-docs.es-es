---
title: "_set_com_error_handler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_com_error_handler (función)"
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# _set_com_error_handler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Reemplaza la función predeterminada que se utiliza para el control de errores de COM.  
  
## Sintaxis  
  
```  
void __stdcall _set_com_error_handler(  
   void (__stdcall *pHandler)(  
      HRESULT hr,   
      IErrorInfo* perrinfo  
   )  
);  
```  
  
#### Parámetros  
 `pHandler`  
 Puntero a la función de reemplazo.  
  
 `hr`  
 Información de `HRESULT`.  
  
 `perrinfo`  
 Objeto `IErrorInfo`.  
  
## Comentarios  
 De forma predeterminada, [\_com\_raise\_error](../cpp/com-raise-error.md) controla todos los errores de COM.  Puede cambiar este comportamiento mediante `_set_com_error_handler` para llamar a su propia función de control de errores.  
  
 La función de reemplazo debe tener una firma que sea equivalente a la de `_com_raise_error`.  
  
## Ejemplo  
  
```  
// _set_com_error_handler.cpp  
// compile with /EHsc  
#include <stdio.h>  
#include <comdef.h>  
#include <comutil.h>  
  
// Importing ado dll to attempt to establish an ado connection.  
// Not related to _set_com_error_handler   
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")  
  
void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)  
{  
   throw "Unable to establish the connection!";  
}  
  
int main()  
{  
   _set_com_error_handler(_My_com_raise_error);  
   _bstr_t bstrEmpty(L"");  
   _ConnectionPtr Connection = NULL;  
   try  
   {  
      Connection.CreateInstance(__uuidof(Connection));  
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);   
   }  
   catch(char* errorMessage)  
   {  
      printf("Exception raised: %s\n", errorMessage);  
   }  
  
   return 0;  
}  
```  
  
  **Se produjo una excepción: no se puede establecer la conexión.**   
## Requisitos  
 **Encabezado:** comdef.h  
  
 **Lib:** si la opción del compilador “wchar\_t es tipo nativo” está activada, use omsuppw.lib o comsuppwd.lib.  Si “wchar\_t es tipo nativo” está desactivada, use comsupp.lib.  Para obtener más información, vea [\/Zc:wchar\_t \(wchar\_t es un tipo nativo\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## Vea también  
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)