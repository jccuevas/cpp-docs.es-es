---
title: _set_com_error_handler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1f516114dbaa9e507491cf669c3371b6b8fbaf11
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944546"
---
# <a name="setcomerrorhandler"></a>_set_com_error_handler
**Específicos de Microsoft**  
  
 Reemplaza la función predeterminada que se utiliza para el control de errores de COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __stdcall _set_com_error_handler(  
   void (__stdcall *pHandler)(  
      HRESULT hr,   
      IErrorInfo* perrinfo  
   )  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pHandler*  
 Puntero a la función de reemplazo.  
  
 *recursos humanos*  
 Información de HRESULT.  
  
 *perrinfo*  
 Objeto `IErrorInfo`.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, [_com_raise_error](../cpp/com-raise-error.md) controla todos los errores de COM. Puede cambiar este comportamiento mediante `_set_com_error_handler` para llamar a su propia función de control de errores.  
  
 La función de reemplazo debe tener una firma que sea equivalente a la de `_com_raise_error`.  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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
  
```Output  
Exception raised: Unable to establish the connection!  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<comdef.h >  
  
 **Lib:** si el **wchar_t es tipo nativo** opción del compilador está activada, use omsuppw.lib o comsuppwd.lib. Si **wchar_t es tipo nativo** está desactivada, use comsupp.lib. Para obtener más información, vea [/Zc:wchar_t (wchar_t es un tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
## <a name="see-also"></a>Vea también  
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)