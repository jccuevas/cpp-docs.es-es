---
title: Uso de atributos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4f44d6e4db7e09033e9c3f05d94cbf5294b306a3
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018287"
---
# <a name="purpose-of-attributes"></a>Objetivo de los atributos
Atributos extensión C++ en direcciones no son actualmente posibles sin romper la estructura clásica del lenguaje. Los atributos permiten a proveedores (DLL independiente) para ampliar la funcionalidad del lenguaje dinámicamente. El objetivo principal de atributos es simplificar la creación de componentes COM, además de aumentar el nivel de productividad del desarrollador de componentes. Los atributos se pueden aplicar a casi cualquier construcción de C++, como clases, miembros de datos o las funciones miembro. Este es un área resaltada de ventajas que ofrece esta nueva tecnología:  
  
-   Expone una convención de llamada simple y familiar.  
  
-   Usa código insertado que, a diferencia de las macros, se reconoce el depurador.  
  
-   Permite la fácil derivación de clases base sin onerosos detalles de implementación.  
  
-   Reemplaza la gran cantidad de código IDL requerido por un componente COM con unos cuantos atributos concisos.  
  
 Por ejemplo, para implementar un receptor de eventos simple para una clase genérica de ATL, podría aplicar el [event_receiver](../windows/event-receiver.md) atributo en una clase específica como `CMyReceiver`. El `event_receiver` , a continuación, se compila el atributo por el compilador de Visual C++, que inserta el código adecuado en el archivo de objeto.  
  
```cpp  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 A continuación, puede configurar el `CMyReceiver` métodos `handler1` y `handler2` para controlar los eventos (mediante la función intrínseca [__hook](../cpp/hook.md)) desde un origen de eventos, puede crear mediante [event_source](../windows/event-source.md).  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../windows/attributed-programming-concepts.md)