---
title: Registerobjects (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterObjects
dev_langs:
- C++
helpviewer_keywords:
- RegisterObjects method
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c9a44fed853fe2f4dcd3196e926b3848566ab4e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597031"
---
# <a name="moduleregisterobjects-method"></a>Module::RegisterObjects (Método)

Registra los objetos COM o en tiempo de ejecución de Windows para que otras aplicaciones pueden conectarse a ellos.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>Parámetros

*módulo*  
Una matriz de objetos COM o en tiempo de ejecución de Windows.

*Nombre de servidor*  
Nombre del servidor que crea los objetos.

## <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un HRESULT que indica el motivo del error en la operación.

## <a name="requirements"></a>Requisitos

**Encabezado:** module.h

**Espacio de nombres:** Microsoft::WRL

## <a name="see-also"></a>Vea también

[Module (clase)](../windows/module-class.md)