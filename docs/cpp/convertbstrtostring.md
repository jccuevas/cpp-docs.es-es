---
title: ConvertBSTRToString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- ConvertBSTRToString
dev_langs:
- C++
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c46ab493c6f3c80d9bee4b4b0c04d9569c12e23c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075889"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString

**Específicos de Microsoft**

Convierte un `BSTR` valor a un `char *`.

## <a name="syntax"></a>Sintaxis

```
char* __stdcall ConvertBSTRToString(BSTR pSrc);
```

#### <a name="parameters"></a>Parámetros

*pSrc*<br/>
Una variable BSTR.

## <a name="remarks"></a>Comentarios

**ConvertBSTRToString** asigna una cadena que se debe eliminar.

## <a name="example"></a>Ejemplo

```cpp
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

```Output
BSTR text: Test
char * text: Test
```

**FIN de Específicos de Microsoft**

## <a name="requirements"></a>Requisitos

**Encabezado:** \<comutil.h >

**Lib:** omsuppw.lib o comsuppwd.lib (vea [/Zc: wchar_t (wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)

## <a name="see-also"></a>Vea también

[Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)