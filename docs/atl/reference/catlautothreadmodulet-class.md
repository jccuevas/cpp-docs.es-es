---
title: CAtlAutoThreadModuleT (clase)
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: 63f1c8dbe3c752773fd64c6e339a9a3b67051d35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62247183"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT (clase)

Esta clase proporciona métodos para implementar un servidor COM de subprocesamiento de modelo, agrupadas por subproceso.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase que implementará el servidor COM.

*ThreadAllocator*<br/>
La clase de administración de selección de subprocesos. El valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Especifica el intervalo de tiempo de espera, en milisegundos. El valor predeterminado es infinito, lo que significa que intervalo de tiempo de espera del método nunca transcurre.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Esta función estática dinámicamente calcula y devuelve el número máximo de subprocesos para el módulo ejecutable, en función del número de procesadores.|

## <a name="remarks"></a>Comentarios

La clase [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) deriva `CAtlAutoThreadModuleT` con el fin de implementar un servidor COM de subprocesamiento de modelo, agrupadas por subproceso. Reemplaza a la clase obsoleta [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
>  Esta clase no debe usarse en un archivo DLL, como el valor predeterminado *dwWait* valor de infinito producirá un interbloqueo cuando se descarga el archivo DLL.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="getdefaultthreads"></a>  CAtlAutoThreadModuleT::GetDefaultThreads

Esta función estática dinámicamente calcula y devuelve el número máximo de subprocesos para el módulo ejecutable, en función del número de procesadores.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valor devuelto

El número de subprocesos que se creará en el módulo del archivo EXE.

### <a name="remarks"></a>Comentarios

Invalide este método si desea usar otro método para calcular el número de subprocesos. De forma predeterminada, el número de subprocesos se basa en el número de procesadores.

## <a name="see-also"></a>Vea también

[IAtlAutoThreadModule (clase)](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[IAtlAutoThreadModule (clase)](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
