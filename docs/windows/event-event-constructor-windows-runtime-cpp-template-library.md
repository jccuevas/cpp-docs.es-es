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
ms.openlocfilehash: 8c2683d2e1875e7d68d27f7bde515b7a4ca70da0
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649733"
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
 *h*  
 Identificador para un evento. De forma predeterminada, *h* se inicializa en **nullptr**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Namespace:** Wrappers  
  
## <a name="see-also"></a>Vea también  
 [Event (clase) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)](../windows/event-class-windows-runtime-cpp-template-library.md)