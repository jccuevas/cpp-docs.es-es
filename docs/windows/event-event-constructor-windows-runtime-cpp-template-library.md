---
title: 'Constructor event:: Event (biblioteca de plantillas C++ de Windows en tiempo de ejecución) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::Event
dev_langs:
- C++
ms.assetid: 21495297-9612-4095-9256-16e168cc0021
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bd9f02935d0d88976fd3b62c7276f106519fa74
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381015"
---
# <a name="eventevent-constructor-windows-runtime-c-template-library"></a>Event::Event Constructor (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)

Inicializa una nueva instancia de la **eventos** clase.

## <a name="syntax"></a>Sintaxis

```cpp
explicit Event(
   HANDLE h = HandleT::Traits::GetInvalidValue()  
);
WRL_NOTHROW Event(
   _Inout_ Event&& h
);
```

### <a name="parameters"></a>Parámetros

*h*<br/>
Identificador para un evento. De forma predeterminada, *h* se inicializa en **nullptr**.

## <a name="requirements"></a>Requisitos

**Encabezado:** corewrappers.h

**Namespace:** Wrappers

## <a name="see-also"></a>Vea también

[Event (clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)](../windows/event-class-windows-runtime-cpp-template-library.md)