---
title: Interfaces (ATL) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0db5a79f187cb0fe320bf67aace751a5d4c537d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="interfaces-atl"></a>Interfaces (ATL)
Una interfaz es la manera en que un objeto expone su funcionalidad al mundo exterior. En COM, una interfaz es una tabla de punteros (como una vtable de C++) a funciones implementadas por el objeto. La tabla representa la interfaz y las funciones a la que señala son los métodos de esa interfaz. Un objeto puede exponer tantas interfaces como elija.  
  
 Cada interfaz se basa en la interfaz COM fundamental, [IUnknown](../atl/iunknown.md). Los métodos de **IUnknown** permiten navegar por otras interfaces expuestas por el objeto.  
  
 Además, cada interfaz tiene un único identificador de interfaz (IID). Esta unicidad facilita la admiten las versiones de interfaz. Una nueva versión de una interfaz es simplemente una nueva interfaz con un nuevo IID.  
  
> [!NOTE]
>  IID de las interfaces de COM y OLE estándares están predefinidos.  
  
## <a name="see-also"></a>Vea también  
 [Introducción a COM](../atl/introduction-to-com.md)   
 [Interfaces y objetos COM](http://msdn.microsoft.com/library/windows/desktop/ms690343)

