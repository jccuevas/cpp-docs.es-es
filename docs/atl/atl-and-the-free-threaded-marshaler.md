---
title: "ATL y el contador de referencias de subprocesamiento libre | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, contador de referencias de subprocesamiento libre"
  - "contador de referencias de subprocesamiento libre"
  - "FTM en ATL"
  - "subprocesamiento [ATL], contador de referencias de subprocesamiento libre"
  - "subprocesamiento [C++], contador de referencias en ATL"
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ATL y el contador de referencias de subprocesamiento libre
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La página atributos ATL Simple del asistente para objetos proporciona una opción que permite que la clase agregue el contador de subproceso libre \(FTM\).  
  
 El asistente genera código para crear una instancia del contador de subproceso libre en `FinalConstruct` y liberar esa instancia en `FinalRelease`.  Una macro de `COM_INTERFACE_ENTRY_AGGREGATE` se agrega automáticamente al mapa COM para garantizar que las solicitudes de `QueryInterface` para [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707) se controlan mediante el contador de subproceso libre.  
  
 El contador de subproceso libre permite acceso directo a las interfaces en un objeto de cualquier subproceso del mismo de proceso, acelerando llamadas de cruce\- apartamento.  Esta opción está pensado para las clases que utilizan el modelo de subprocesos de Both.  
  
 Con esta opción, las clases deben asumir la responsabilidad de la seguridad para subprocesos de sus datos.  Además, se opone que agrega el contador de subproceso libre y la necesidad de utilizar los punteros de interfaz obtenidos de otros objetos debe pasos adicionales para asegurarse de que las interfaces correctamente se calculen las referencias.  Esto implica normalmente el almacenamiento de punteros de interfaz en la tabla global \(GIT\) de la interfaz y el obtener del puntero de GIT cada vez que se utiliza.  ATL proporciona la clase [CComGITPtr](../atl/reference/ccomgitptr-class.md) para ayudarle a utilizar los punteros de interfaz almacenados en el GIT.  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)   
 [CoCreateFreeThreadedMarshaler](http://msdn.microsoft.com/library/windows/desktop/ms694500)   
 [IMarshal](http://msdn.microsoft.com/library/windows/desktop/dd542707)   
 [When to Use the Global Interface Table](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [In\-Process Server Threading Issues](http://msdn.microsoft.com/library/windows/desktop/ms687205)