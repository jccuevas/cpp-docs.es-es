---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: 864236e86b4aeb6ce7b3315df57af1b577693c26
ms.sourcegitcommit: f127b08f114b8d6cab6b684febcb6f2ae0e055ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954944"
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

*pHandler*<br/>
Puntero a la función de reemplazo.

*hr*<br/>
Información de HRESULT.

*perrinfo*<br/>
Objeto `IErrorInfo`.

## <a name="remarks"></a>Comentarios

De forma predeterminada, [_com_raise_error](../cpp/com-raise-error.md) controla todos los errores de COM. Puede cambiar este comportamiento mediante **_set_com_error_handler** para llamar a su propia función de control de errores.

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

**Lib:** Si el **/Zc:** se especificó la opción del compilador (valor predeterminado), use omsuppw.lib o comsuppwd.lib. Si el **/Zc:wchar_t-** se especificó la opción del compilador, utilice comsupp.lib. Para obtener más información, incluida la forma de establecer esta opción en el IDE, vea [/Zc: wchar_t (wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Vea también

[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)
