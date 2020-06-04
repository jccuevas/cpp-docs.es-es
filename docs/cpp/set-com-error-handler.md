---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: debad733f351c710ada342e29fa95a4d1ff03b7d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749798"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

Reemplaza la función predeterminada que se utiliza para el control de errores de COM. **_set_com_error_handler** es específica de Microsoft.

## <a name="syntax"></a>Sintaxis

```cpp
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

*Hr*<br/>
Información de HRESULT.

*perrinfo*<br/>
Objeto `IErrorInfo`.

## <a name="remarks"></a>Observaciones

De forma predeterminada, [_com_raise_error](../cpp/com-raise-error.md) controla todos los errores COM. Puede cambiar este comportamiento mediante **_set_com_error_handler** para llamar a su propia función de control de errores.

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

**Encabezado:** \<> comdef.h

**Lib:** Si se especifica la opción del compilador **/Zc:wchar_t** (valor predeterminado), utilice comsuppw.lib o comsuppwd.lib. Si se especifica la opción del compilador **/Zc:wchar_t-,** utilice comsupp.lib. Para obtener más información, incluido cómo establecer esta opción en el IDE, vea [/Zc:wchar_t (wchar_t es tipo nativo).](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>Vea también

[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)
