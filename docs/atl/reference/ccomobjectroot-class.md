---
title: CComObjectRoot (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
dev_langs:
- C++
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2647ea3ac46ec3783f584de996c3d988c168980d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054868"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot (clase)

Esta definición de tipo de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) se hace plantilla en el modelo del servidor de subprocesamiento predeterminado.

## <a name="syntax"></a>Sintaxis

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>Comentarios

`CComObjectRoot` es un `typedef` de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) hace plantilla en el modelo del servidor de subprocesamiento predeterminado. Por lo tanto [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) hará referencia alguno [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) o [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).

`CComObjectRootEx` controla la administración de recuento de referencia de objeto para objetos agregados y agregados. Si no se agrega el objeto y mantiene el puntero para el desconocido externo si se agrega el objeto contiene el recuento de referencias de objeto. Para los objetos agregados, `CComObjectRootEx` métodos que pueden usarse para controlar el error del objeto interno para construir y se elimina proteger el objeto contra eliminación cuando se publican las interfaces internas externo o el objeto interno.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="see-also"></a>Vea también

[CComObjectRootEx (clase)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject (clase)](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject (clase)](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject (clase)](../../atl/reference/ccompolyobject-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
