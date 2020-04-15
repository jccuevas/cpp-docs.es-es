---
title: Funciones globales de WinModule
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
ms.openlocfilehash: 3d7d001a2835514cc5385a7069c0bcda58cdd88e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329357"
---
# <a name="winmodule-global-functions"></a>Funciones globales de WinModule

Estas funciones `_AtlCreateWndData` proporcionan compatibilidad con operaciones de estructura.

> [!IMPORTANT]
> Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

|||
|-|-|
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Esta función se utiliza para inicializar y agregar una estructura `_AtlCreateWndData`.|
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Llame a esta función para extraer una estructura `_AtlCreateWndData` existente.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="atlwinmoduleaddcreatewnddata"></a><a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData

Esta función se utiliza para inicializar y agregar una estructura `_AtlCreateWndData`.

```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```

### <a name="parameters"></a>Parámetros

*pWinModule*<br/>
Puntero a la estructura [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) de un módulo.

*pData*<br/>
Puntero a la [estructura _AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) que se va a inicializar y agregar al módulo actual.

*pObject*<br/>
Puntero a un objeto **de este** puntero.

### <a name="remarks"></a>Observaciones

Inicializa una `_AtlCreateWndData` estructura, que se utiliza para almacenar el puntero **this** utilizado para hacer referencia a instancias de clase, y lo agrega a la lista a la que hace referencia la estructura de `_ATL_WIN_MODULE70` un módulo. Llamado por [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).

## <a name="atlwinmoduleextractcreatewnddata"></a><a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData

Llame a esta función para extraer una estructura `_AtlCreateWndData` existente.

```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```

### <a name="parameters"></a>Parámetros

*pWinModule*<br/>
Puntero a la estructura [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) de un módulo.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la [estructura _AtlCreateWndData.](../../atl/reference/atlcreatewnddata-structure.md)

### <a name="remarks"></a>Observaciones

Esta función extraerá una estructura existente `_AtlCreateWndData` de `_ATL_WIN_MODULE70` la lista a la que hace referencia la estructura de un módulo.

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)
