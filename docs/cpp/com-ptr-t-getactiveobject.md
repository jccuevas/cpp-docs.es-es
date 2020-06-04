---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: ea8059a039b77811dd54d4a4937ad746b7ca0937
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170806"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Específicos de Microsoft**

Se adjunta a una instancia existente de un objeto, dado un `CLSID` o `ProgID`.

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
`CLSID` de un objeto.

*clsidString*<br/>
Cadena Unicode que contiene un `CLSID` (a partir de " **{** ") o un `ProgID`.

*clsidStringA*<br/>
Una cadena multibyte, mediante la página de códigos ANSI, que contiene un `CLSID` (a partir de " **{** ") o un `ProgID`.

## <a name="remarks"></a>Observaciones

Estas funciones miembro llaman a **GetActiveObject** para recuperar un puntero a un objeto en ejecución que se ha registrado con OLE y, a continuación, consulta para el tipo de interfaz de este puntero inteligente. El puntero resultante se encapsula dentro de este objeto `_com_ptr_t`. se llama a `Release` para reducir el recuento de referencias del puntero encapsulado previamente. Esta rutina devuelve HRESULT para indicar si se ha realizado correctamente o no.

- **GetActiveObject (** `rclsid` **)** Se adjunta a una instancia existente de un objeto a partir de un `CLSID`.

- **GetActiveObject (** `clsidString` **)** Se adjunta a una instancia existente de un objeto dada una cadena Unicode que contiene un `CLSID` (a partir de " **{** ") o un `ProgID`.

- **GetActiveObject (** `clsidStringA` **)** Se adjunta a una instancia existente de un objeto, dada una cadena de caracteres multibyte que contiene un `CLSID` (a partir de " **{** ") o un `ProgID`. Llama a [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), que supone que la cadena está en la página de códigos ANSI en lugar de en una página de códigos OEM.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[_com_ptr_t (Clase)](../cpp/com-ptr-t-class.md)
