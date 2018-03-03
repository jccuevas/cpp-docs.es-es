---
title: Error del compilador C2338 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0171654bde5b056a7e6695ea5fbbe84edb62f83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2338"></a>Error del compilador C2338  
  
> *Mensaje de error*  
  
Este error puede deberse a un `static_assert` error durante la compilación. El mensaje proporcionado por el `static_assert` parámetros.   
  
Este mensaje de error también puede generarse por proveedores externos al compilador. En la mayoría de los casos, estos errores notificados por un proveedor de atributos de archivo DLL, por ejemplo, ATLPROV. Algunas formas comunes de este mensaje se incluyen:

> '*atributo*' proveedor de atributos Atl: error ATL*número* *mensaje*  
  
> Uso incorrecto del atributo '*atributo*'
  
> '*uso*': un formato incorrecto para el atributo 'uso'  
  
Estos errores suelen ser irrecuperables y pueden ir seguidos de un error grave del compilador.  
  
Para corregir estos problemas, corrija el uso de atributos. Por ejemplo, en algunos casos, los parámetros de atributo deben declararse antes de que se puedan utilizar. Si no se proporciona un número de error ATL, consulte la documentación para dicho error para obtener información más detallada.  
