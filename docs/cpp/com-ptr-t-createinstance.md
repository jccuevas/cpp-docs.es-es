---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 82b180b3f40683495ed2cfa284bdae8e1afaef9e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498660"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Específicos de Microsoft**

Crea una nueva instancia de un objeto, dado `CLSID` un `ProgID`o.

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
`CLSID` De un objeto.

*clsidString*<br/>
Cadena Unicode que contiene un (a `CLSID` partir de " **{** ") o un `ProgID`.

*clsidStringA*<br/>
Una cadena multibyte, mediante la página de códigos ANSI, que contiene `CLSID` (empezando por " **{** `ProgID`") o.

*dwClsContext*<br/>
Contexto para el código ejecutable.

*pOuter*<br/>
El externo desconocido para la [agregación](../atl/aggregation.md).

## <a name="remarks"></a>Comentarios

Estas funciones de miembro llaman a `CoCreateInstance` para crear un nuevo objeto CM y, a continuación, consultas para el tipo de interfaz de este puntero inteligente. El puntero resultante se encapsula dentro de este objeto `_com_ptr_t`. `Release`se llama a para reducir el recuento de referencias del puntero encapsulado previamente. Esta rutina devuelve HRESULT para indicar si se ha realizado correctamente o no.

- **CreateInstance (** *rclsid* **,** *dwClsContext* **)** Crea una nueva instancia en ejecución de un objeto, `CLSID`dado un.

- **CreateInstance (** *clsidString* **,** *dwClsContext* **)** Crea una nueva instancia en ejecución de un objeto, dada una cadena Unicode que contiene `CLSID` (a partir de " **{** `ProgID`") o.

- **CreateInstance (** *clsidStringA* **,** *dwClsContext* **)** Crea una nueva instancia en ejecución de un objeto a partir de una cadena de caracteres multibyte `CLSID` que contiene (a partir de " **{** `ProgID`") o. Llama a [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), que supone que la cadena está en la página de códigos ANSI en lugar de en una página de códigos OEM.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)