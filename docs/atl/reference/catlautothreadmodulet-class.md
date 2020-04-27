---
title: Clase CAtlAutoThreadModuleT
ms.date: 11/04/2016
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
ms.openlocfilehash: 7308e3a51c531fbe942e2df326c03273eeb326e2
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168729"
---
# <a name="catlautothreadmodulet-class"></a>Clase CAtlAutoThreadModuleT

Esta clase proporciona métodos para implementar un servidor COM de modelo de apartamento y agrupado de subprocesos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T,
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase que implementará el servidor COM.

*ThreadAllocator*<br/>
La clase que administra la selección del subproceso. El valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Especifica el intervalo de tiempo de espera, en milisegundos. El valor predeterminado es infinito, lo que significa que el intervalo de tiempo de espera del método nunca transcurre.

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Esta función estática calcula y devuelve dinámicamente el número máximo de subprocesos para el módulo EXE, en función del número de procesadores.|

## <a name="remarks"></a>Observaciones

La clase [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) deriva de `CAtlAutoThreadModuleT` para implementar un servidor com de modelo de apartamento y agrupado de subprocesos. Reemplaza la clase obsoleta [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
> Esta clase no se debe usar en un archivo DLL, ya que el valor predeterminado de *dwWait* de Infinite producirá un interbloqueo cuando se descargue el archivo dll.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads

Esta función estática calcula y devuelve dinámicamente el número máximo de subprocesos para el módulo EXE, en función del número de procesadores.

```cpp
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valor devuelto

Número de subprocesos que se van a crear en el módulo EXE.

### <a name="remarks"></a>Observaciones

Invalide este método si desea utilizar un método diferente para calcular el número de subprocesos. De forma predeterminada, el número de subprocesos se basa en el número de procesadores.

## <a name="see-also"></a>Consulte también

[Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
