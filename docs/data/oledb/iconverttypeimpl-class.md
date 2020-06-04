---
title: IConvertTypeImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
- IConvertTypeImpl.CanConvert
- CanConvert
- IConvertTypeImpl::CanConvert
helpviewer_keywords:
- IConvertTypeImpl class
- CanConvert method
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
ms.openlocfilehash: e3b76be2a1f1edfcdc1139a3dd396835923c2b4a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210696"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl (Clase)

Proporciona una implementación de la interfaz [IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IConvertTypeImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[CanConvert](#canconvert)|Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.|

## <a name="remarks"></a>Observaciones

Esta interfaz es obligatoria en los comandos, conjuntos de filas y conjuntos de filas de índice. `IConvertTypeImpl` implementa la interfaz delegando en el objeto de conversión proporcionado por OLE DB.

## <a name="iconverttypeimplcanconvert"></a><a name="canconvert"></a>Iconverttypeimpl (:: CanConvert

Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Parámetros

Vea [IConvertType:: CanConvert](/previous-versions/windows/desktop/ms711224(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Usa la conversión de datos OLE DB en `MSADC.DLL`.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
