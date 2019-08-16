---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: f13a42878392f63096cdfcb405f3f91cc0efe451
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498888"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Específicos de Microsoft**

Se adjunta a una instancia existente de un objeto, dado `CLSID` un `ProgID`o.

## <a name="syntax"></a>Sintaxis

```
HRESULT GetActiveObject(
   const CLSID& rclsid
) throw( );
HRESULT GetActiveObject(
   LPCWSTR clsidString
) throw( );
HRESULT GetActiveObject(
   LPCSTR clsidStringA
) throw( );
```

#### <a name="parameters"></a>Parámetros

*rclsid*<br/>
`CLSID` De un objeto.

*clsidString*<br/>
Cadena Unicode que contiene un (a `CLSID` partir de " **{** ") o un `ProgID`.

*clsidStringA*<br/>
Una cadena multibyte, mediante la página de códigos ANSI, que contiene `CLSID` (empezando por " **{** `ProgID`") o.

## <a name="remarks"></a>Comentarios

Estas funciones miembro llaman a **GetActiveObject** para recuperar un puntero a un objeto en ejecución que se ha registrado con OLE y, a continuación, consulta para el tipo de interfaz de este puntero inteligente. El puntero resultante se encapsula dentro de este objeto `_com_ptr_t`. `Release`se llama a para reducir el recuento de referencias del puntero encapsulado previamente. Esta rutina devuelve HRESULT para indicar si se ha realizado correctamente o no.

- **GetActiveObject (** `rclsid` **)** se adjunta a una instancia existente de un objeto, dado `CLSID`un.

- **GetActiveObject (** `clsidString` **)** se adjunta a una instancia existente de un objeto, dada una cadena Unicode que contiene ( `CLSID` a `ProgID`partir de " **{** ") o.

- **GetActiveObject (** `clsidStringA` **)** se adjunta a una instancia existente de un objeto, dada una cadena de caracteres multibyte que contiene `CLSID` (a `ProgID`partir de " **{** ") o. Llama a [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), que supone que la cadena está en la página de códigos ANSI en lugar de en una página de códigos OEM.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)