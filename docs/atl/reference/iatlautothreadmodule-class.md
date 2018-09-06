---
title: IAtlAutoThreadModule (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAtlAutoThreadModule
- atlbase/ATL::IAtlAutoThreadModule
dev_langs:
- C++
helpviewer_keywords:
- IAtlAutoThreadModule class
ms.assetid: fcb58cf9-a427-4be9-89eb-04e1ab5cc3a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c5d92eb693a73aff20ff8869be4412574a15cbe
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764366"
---
# <a name="iatlautothreadmodule-class"></a>IAtlAutoThreadModule (clase)

Esta clase representa una interfaz para un `CreateInstance` método.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
__interface IAtlAutoThreadModule
```

## <a name="remarks"></a>Comentarios

La clase [CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md) deriva `IAtlAutoThreadModule`, usarlo para proporcionar código para crear un objeto y recuperar un puntero de interfaz.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
