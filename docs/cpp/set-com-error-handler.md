---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: 226dce24de68edd66ca68c43e41ce0cb5b8a1b48
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857299"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

Reemplaza la función predeterminada que se utiliza para el control de errores de COM. **_set_com_error_handler** es específico de Microsoft.

## <a name="syntax"></a>Sintaxis

```
void __stdcall _set_com_error_handler(
   void (__stdcall *pHandler)(
      HRESULT hr,
      IErrorInfo* perrinfo
   )
);
```

#### <a name="parameters"></a>Parameters

*pHandler*<br/>
Puntero a la función de reemplazo.

*hr*<br/>
Información de HRESULT.

*perrinfo*<br/>
`IErrorInfo` existente.

## <a name="remarks"></a>Notas

De forma predeterminada, [_com_raise_error](../cpp/com-raise-error.md) controla todos los errores de com. Puede cambiar este comportamiento mediante el uso de **_set_com_error_handler** para llamar a su propia función de control de errores.

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

## <a name="requirements"></a>Requisitos de

**Encabezado:** \<comdef. h >

**Lib:** Si se especifica la opción del compilador **/Zc: wchar_t** (valor predeterminado), use omsuppw. lib o comsuppwd. lib. Si se especifica la opción de compilador **/Zc: wchar_t** , use comsupp. lib. Para obtener más información, incluida la forma de establecer esta opción en el IDE, vea [/Zc: wchar_t (Wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

## <a name="see-also"></a>Vea también

[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)
