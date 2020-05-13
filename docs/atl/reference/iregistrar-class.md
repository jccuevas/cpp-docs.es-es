---
title: Interfaz IRegistrar
ms.date: 02/01/2017
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
ms.openlocfilehash: 98943fe294322715723bd91207a6f3320ca1ffb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329467"
---
# <a name="iregistrar-interface"></a>Interfaz IRegistrar

Esta interfaz se define en atliface.h y se utiliza internamente en funciones miembro CAtlModule como [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).

## <a name="syntax"></a>Sintaxis

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>Observaciones

Consulte el tema Uso de [parámetros reemplazables (preprocesador del registrador)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) para obtener más detalles.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Registra el recurso. |
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Anula el registro del recurso.|
|[IRegistrar::FileRegister](#fileregister)|Registra el archivo.|
|[IRegistrar::FileUnregister](#fileunregister)|Anula el registro del archivo.|
|[IRegistrar::StringRegister](#stringregister)|Registra la cadena.|
|[IRegistrar::StringUnregister](#stringunregister)|Anula el registro de la cadena|
|[IRegistrar::ResourceRegister](#resourceregister)|Registra el recurso.|
|[IRegistrar::ResourceUnregister](#resourceunregister)|Anula el registro del recurso.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlifase.h

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a>IRegistrar::ResourceRegisterSz

Registra el recurso.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a>IRegistrar::ResourceUnregisterSz

Anula el registro del recurso.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a>IRegistrar::FileRegister

Registra el archivo.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a>IRegistrar::FileUnregister

Anula el registro del archivo.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a>IRegistrar::StringRegister

Registra los datos de cadena especificados.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a>IRegistrar::StringUnregister

Anula el registro de los datos de cadena especificados.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a>IRegistrar::ResourceRegister

Registra el recurso.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a>IRegistrar::ResourceUnregister

Anula el registro del recurso.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>Consulte también

[Uso de parámetros reemplazables (preprocesador del registrador)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)<br/>
[Componente de registro (Registrador)](../../atl/atl-registry-component-registrar.md)
