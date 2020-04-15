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
ms.openlocfilehash: e7b7a327d7c47c4472b43ed58fbe9ad0556a7620
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321541"
---
# <a name="catlautothreadmodulet-class"></a>Clase CAtlAutoThreadModuleT

Esta clase proporciona métodos para implementar un servidor COM de modelo de apartamento con grupo de subprocesos.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

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
La clase que administra la selección de subprocesos. El valor predeterminado es [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

*dwWait*<br/>
Especifica el intervalo de tiempo de espera, en milisegundos. El valor predeterminado es INFINITE, lo que significa que el intervalo de tiempo de espera del método nunca transcurre.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Esta función estática calcula y devuelve dinámicamente el número máximo de subprocesos para el módulo EXE, en función del número de procesadores.|

## <a name="remarks"></a>Observaciones

La clase [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) `CAtlAutoThreadModuleT` deriva para implementar un servidor COM de modelo de apartamento con grupo de subprocesos. Reemplaza la clase obsoleta [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

> [!NOTE]
> Esta clase no se debe utilizar en un archivo DLL, ya que el valor *dwWait* predeterminado de INFINITE provocará un interbloqueo cuando se descargue el archivo DLL.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`IAtlAutoThreadModule`

`CAtlAutoThreadModuleT`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="catlautothreadmoduletgetdefaultthreads"></a><a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads

Esta función estática calcula y devuelve dinámicamente el número máximo de subprocesos para el módulo EXE, en función del número de procesadores.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Valor devuelto

El número de subprocesos que se crearán en el módulo EXE.

### <a name="remarks"></a>Observaciones

Invalide este método si desea utilizar un método diferente para calcular el número de subprocesos. De forma predeterminada, el número de subprocesos se basa en el número de procesadores.

## <a name="see-also"></a>Consulte también

[Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)<br/>
[Clases de módulo](../../atl/atl-module-classes.md)
