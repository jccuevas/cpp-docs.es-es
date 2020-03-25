---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 2ec4e90c8f0c1009cc47e9022a09b3b8f7dbb284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190006"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Específicos de Microsoft**

Crea una nueva instancia de un objeto a partir de un `CLSID` o `ProgID`.

## <a name="syntax"></a>Sintaxis

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>Parámetros

*rclsid*<br/>
`CLSID` de un objeto.

*clsidString*<br/>
Cadena Unicode que contiene un `CLSID` (a partir de " **{** ") o un `ProgID`.

*clsidStringA*<br/>
Una cadena multibyte, mediante la página de códigos ANSI, que contiene un `CLSID` (a partir de " **{** ") o un `ProgID`.

*dwClsContext*<br/>
Contexto para el código ejecutable.

*pOuter*<br/>
El externo desconocido para la [agregación](../atl/aggregation.md).

## <a name="remarks"></a>Observaciones

Estas funciones de miembro llaman a `CoCreateInstance` para crear un nuevo objeto CM y, a continuación, consultas para el tipo de interfaz de este puntero inteligente. El puntero resultante se encapsula dentro de este objeto `_com_ptr_t`. se llama a `Release` para reducir el recuento de referencias del puntero encapsulado previamente. Esta rutina devuelve HRESULT para indicar si se ha realizado correctamente o no.

- **CreateInstance (**  *rclsid* **,**  *dwClsContext*  **)** Crea una nueva instancia en ejecución de un objeto a partir de un `CLSID`.

- **CreateInstance (**  *clsidString* **,**  *dwClsContext*  **)** Crea una nueva instancia en ejecución de un objeto dada una cadena Unicode que contiene un `CLSID` (a partir de " **{** ") o un `ProgID`.

- **CreateInstance (**  *clsidStringA* **,**  *dwClsContext*  **)** Crea una nueva instancia en ejecución de un objeto dada una cadena de caracteres multibyte que contiene un `CLSID` (a partir de " **{** ") o un `ProgID`. Llama a [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), que supone que la cadena está en la página de códigos ANSI en lugar de en una página de códigos OEM.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
