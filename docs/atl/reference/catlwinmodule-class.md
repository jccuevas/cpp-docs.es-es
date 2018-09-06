---
title: CAtlWinModule (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlWinModule
- ATLBASE/ATL::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::CAtlWinModule
- ATLBASE/ATL::CAtlWinModule::AddCreateWndData
- ATLBASE/ATL::CAtlWinModule::ExtractCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e52f21eea272f34bdc6594dcdb8f57c8538ac50
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761291"
---
# <a name="catlwinmodule-class"></a>CAtlWinModule (clase)

Esta clase proporciona compatibilidad para los componentes de ventana ATL.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAtlWinModule : public _ATL_WIN_MODULE
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|El constructor.|
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Agrega un objeto de datos.|
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Devuelve un puntero al objeto de datos del módulo de ventana.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona compatibilidad para todas las clases ATL que requieren características de la ventana.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)

`CAtlWinModule`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="addcreatewnddata"></a>  CAtlWinModule::AddCreateWndData

Este método inicializa y agrega un `_AtlCreateWndData` estructura.

```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```

### <a name="parameters"></a>Parámetros

*pData*  
Puntero a la `_AtlCreateWndData` estructura se inicialicen y agregado al módulo actual.

*pObject*  
Puntero a un objeto **esto** puntero.

### <a name="remarks"></a>Comentarios

Este método llama a [AtlWinModuleAddCreateWndData](winmodule-global-functions.md#atlwinmoduleaddcreatewnddata) que inicializa un [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) estructura. Esta estructura se almacenará el **esto** puntero, utilizado para obtener la instancia de clase en los procedimientos de ventana.

##  <a name="catlwinmodule"></a>  CAtlWinModule::CAtlWinModule

El constructor.

```
CAtlWinModule();
```

### <a name="remarks"></a>Comentarios

Si se produce un error de inicialización, una **EXCEPTION_NONCONTINUABLE** se produce la excepción.

##  <a name="dtor"></a>  CAtlWinModule:: ~ CAtlWinModule

Destructor.

```
~CAtlWinModule();
```

### <a name="remarks"></a>Comentarios

Libera todos los recursos asignados.

##  <a name="extractcreatewnddata"></a>  CAtlWinModule::ExtractCreateWndData

Este método devuelve un puntero a un `_AtlCreateWndData` estructura.

```
void* ExtractCreateWndData();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la `_AtlCreateWndData` estructura agregado previamente con [CAtlWinModule::AddCreateWndData](#addcreatewnddata), o NULL si no hay ningún objeto está disponible.

## <a name="see-also"></a>Vea también

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)   
[Información general de clases](../../atl/atl-class-overview.md)   
[Clases de módulo](../../atl/atl-module-classes.md)
