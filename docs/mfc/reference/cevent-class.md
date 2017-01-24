---
title: "CEvent Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CEvent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEvent class"
  - "clases de sincronización, CEvent class"
  - "synchronization objects, event"
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
caps.latest.revision: 27
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEvent Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un evento, que es un objeto de sincronización que permite que un subproceso para notificar a otro que se ha producido un evento.  
  
## Sintaxis  
  
```  
class CEvent : public CSyncObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CEvent::CEvent](../Topic/CEvent::CEvent.md)|Crea un objeto `CEvent`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CEvent::PulseEvent](../Topic/CEvent::PulseEvent.md)|Establece el evento en los subprocesos en espera disponibles \(notifican\), de las versiones, y establece el evento a ocupada \(nonsignaled\).|  
|[CEvent::ResetEvent](../Topic/CEvent::ResetEvent.md)|Establece el evento en ocupada \(nonsignaled\).|  
|[CEvent::SetEvent](../Topic/CEvent::SetEvent.md)|Establece el evento en disponibles \(designado\) y los libera cualquier subproceso en espera.|  
|[CEvent::Unlock](../Topic/CEvent::Unlock.md)|Libera el objeto de evento.|  
  
## Comentarios  
 Los eventos son útiles cuando un subproceso debe saber cuándo realizar la tarea.  Por ejemplo, un subproceso que copia datos a un archivo de datos debe recibir una notificación cuando los nuevos datos está disponible.  Utilizando un objeto de `CEvent` para notificar la copia subproceso cuando los nuevos datos disponible, el subproceso puede realizar la tarea lo más rápidamente posible.  
  
 los objetos de`CEvent` tienen dos tipos: manual y automático.  
  
 Un objeto automático de `CEvent` cambia automáticamente un estado \(no disponible\) no señalado después de que al menos un subproceso se libere.  De forma predeterminada, un objeto de `CEvent` es automática a menos que pase `TRUE` para el parámetro de `bManualReset` durante la construcción.  
  
 Un objeto de `CEvent` de manual permanece en el estado establecida por [SetEvent](../Topic/CEvent::SetEvent.md) o [ResetEvent](../Topic/CEvent::ResetEvent.md) hasta que se llama a otra función.  para crear un objeto manual de `CEvent` , pase `TRUE` para el parámetro de `bManualReset` durante la construcción.  
  
 Para utilizar un objeto de `CEvent` , cree el objeto de `CEvent` cuando sea necesario.  Especifique el nombre del evento que desea esperar, y también especifíquelo que la aplicación debe poseerlo inicialmente.  Podrá obtener acceso al evento cuando el constructor devuelve.  Llame a [SetEvent](../Topic/CEvent::SetEvent.md) para informes \(está disponible\) el objeto de evento y después llamar a [Unlock](../Topic/CEvent::Unlock.md) cuando termine teniendo acceso al recurso controlado.  
  
 Un método alternativo para utilizar los objetos de `CEvent` es agregar una variable de `CEvent` escrito como un miembro de datos a la clase que desea supervisar.  Durante la construcción del objeto controlado, llame al constructor del miembro de datos de `CEvent` y especifíquelo si el evento se notificará inicialmente, así como tipo de specifythe de objeto del evento que desea, el nombre del evento \(si utiliza los límites de un proceso\), y cualquier atributo de seguridad desee.  
  
 Para tener acceso a un recurso controlado por un objeto de `CEvent` de esta manera, primero cree una variable de [CSingleLock](../../mfc/reference/csinglelock-class.md) tipo o escriba [CMultiLock](../../mfc/reference/cmultilock-class.md) en el método de acceso de recursos.  Llamar a continuación al método de `Lock` de objeto de bloqueo \(por ejemplo, [CMultiLock:: bloqueo](../Topic/CMultiLock::Lock.md)\).  En este punto, el subproceso accederá el recurso, espere a que el recurso sea liberado y accederá, o esperará el recurso que se produce al mercado, el tiempo de espera, y el error para obtener acceso al recurso.  En cualquier caso, el recurso se ha tenido acceso de una manera segura para subprocesos.  Para liberar el recurso, llame a `SetEvent` para informar del objeto de evento, y utilice el método de `Unlock` de objeto de bloqueo \(por ejemplo, [CMultiLock:: Unlock](../Topic/CMultiLock::Unlock.md)\), o deje el objeto de bloqueo situarse fuera de ámbito.  
  
 Para obtener más información sobre cómo utilizar los objetos de `CEvent` , vea [Subprocesamiento múltiple: Uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## Ejemplo  
 [!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/CPP/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/CPP/cevent-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## Requisitos  
 **encabezado:** afxmt.h  
  
## Vea también  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)