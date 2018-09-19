---
title: Unregistercomobject (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterCOMObject
dev_langs:
- C++
helpviewer_keywords:
- UnregisterCOMObject method
ms.assetid: 5d377525-0385-482a-a215-6e8a1f032861
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3409e0e2c1cac5f3934902523edd2653839989ed
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575763"
---
# <a name="moduleunregistercomobject-method"></a>Module::UnregisterCOMObject (Método)

Anula el registro de uno o más objetos COM, lo que impide que otras aplicaciones que se conecten a ellos.

## <a name="syntax"></a>Sintaxis

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>Parámetros

*Nombre de servidor*  
(Sin usar)

*Cookies*  
Una matriz de punteros a valores que identifican los objetos de clase va a anular. La matriz creada por el [RegisterCOMObject](../windows/module-registercomobject-method.md) método.

*count*  
El número de clases para anular el registro.

## <a name="return-value"></a>Valor devuelto

S_OK si esta operación se realiza correctamente; en caso contrario, un error HRESULT que indica el motivo por el error en la operación.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también
[Module (clase)](../windows/module-class.md)