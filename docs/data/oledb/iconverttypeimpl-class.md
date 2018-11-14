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
ms.openlocfilehash: 0b3c0f239b3c80d0b4d3c8425b03a3612a0e6db2
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556236"
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl (Clase)

Proporciona una implementación de la [IConvertType](https://docs.microsoft.com/previous-versions/windows/desktop/ms715926(v=vs.85)) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
class ATL_NO_VTABLE IConvertTypeImpl
   : public IConvertType, public CConvertHelper
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de `IConvertTypeImpl`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[CanConvert](#canconvert)|Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.|

## <a name="remarks"></a>Comentarios

Esta interfaz es obligatoria en los comandos, los conjuntos de filas y conjuntos de filas de índice. `IConvertTypeImpl` implementa la interfaz mediante la delegación para el objeto de conversión proporcionado por OLE DB.

## <a name="canconvert"></a> Iconverttypeimpl:: CanConvert

Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD(CanConvert)(DBTYPE wFromType,
   DBTYPE wToType,
   DBCONVERTFLAGS dwConvertFlags);
```

#### <a name="parameters"></a>Parámetros

Consulte [IConvertType::CanConvert](https://docs.microsoft.com/previous-versions/windows/desktop/ms711224(v=vs.85)) en el *referencia del programador OLE DB*.

### <a name="remarks"></a>Comentarios

Utiliza la conversión de datos OLE DB en `MSADC.DLL`.

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)