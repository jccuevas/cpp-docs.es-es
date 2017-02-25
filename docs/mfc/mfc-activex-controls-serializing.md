---
title: "Controles ActiveX MFC: Serializar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_wVerMinor"
  - "DoPropExchange"
  - "_wVerMajor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoPropExchange (método)"
  - "ExchangeVersion (método)"
  - "GetVersion (método)"
  - "controles ActiveX en MFC, serializar"
  - "controles ActiveX en MFC, compatibilidad de versiones"
  - "controlar las versiones de controles ActiveX"
  - "wVerMajor (constante global)"
  - "wVerMinor (constante global)"
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Controles ActiveX MFC: Serializar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo serializar un control ActiveX.  La serialización es el proceso de lectura de o de la escritura en un medio de almacenamiento persistente, como un archivo de disco.  La biblioteca de \(MFC\) de la clase de la base de Microsoft proporciona compatibilidad integrada para la serialización en la clase `CObject`.  `COleControl` extiende esta compatibilidad a controles ActiveX mediante el uso de un mecanismo de intercambio de propiedad.  
  
 La serialización de los controles ActiveX se implementa invalidando [COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md).  Esta función, denominada durante la carga y el guardado de objeto del control, almacena todas las propiedades implementadas con una variable miembro o una variable miembro con la notificación.  
  
 Los temas siguientes se tratan los puntos principales relacionados con la serialización de un control ActiveX:  
  
-   Implementar `DoPropExchange` funciona para serializar el objeto de control  
  
-   [Personalizar el proceso de serialización](#_core_customizing_the_default_behavior_of_dopropexchange)  
  
-   [Implementar el control de versiones](#_core_implementing_version_support)  
  
##  <a name="_core_implementing_the_dopropexchange_function"></a> Implementar la función de DoPropExchange  
 Cuando se utiliza el asistente para controles ActiveX para generar el proyecto de control, varias funciones predeterminadas de controlador se agregan automáticamente a la clase de control, incluida la implementación predeterminada de [COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md).  El ejemplo siguiente se muestra el código agregado a las clases creadas con el asistente para controles ActiveX:  
  
 [!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_1.cpp)]  
  
 Si desea crear una propiedad persistente, modifique `DoPropExchange` agregando una llamada a la función de intercambio de propiedad.  El ejemplo siguiente se muestra la serialización de una propiedad booleana personalizada de CircleShape, donde la propiedad de CircleShape tiene un valor predeterminado de **VERDADERO**:  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_3.cpp)]  
  
 La tabla siguiente se enumeran las funciones posibles de intercambio de propiedad que se puede utilizar para serializar las propiedades del control:  
  
|Funciones de intercambio de propiedad|Objetivo|  
|-------------------------------------------|--------------|  
|**PX\_Blob \(\)**|Serializa una propiedad de los datos de \(BLOB\) de objeto binario grande de tipo.|  
|**PX\_Bool \(\)**|Serializa una propiedad boolean de tipo.|  
|**PX\_Color \(\)**|Serializa una propiedad color del tipo.|  
|**PX\_Currency \(\)**|Serializa una propiedad de **CY** de tipo \(moneda\).|  
|**PX\_Double \(\)**|Serializa una propiedad de **double** de tipo.|  
|**PX\_Font \(\)**|Serializa una propiedad de tipo de fuente.|  
|**PX\_Float \(\)**|Serializa una propiedad de **flotante** de tipo.|  
|**PX\_IUnknown \(\)**|Serializa una propiedad de `LPUNKNOWN`escrito.|  
|**PX\_Long \(\)**|Serializa una propiedad de **long** de tipo.|  
|**PX\_Picture \(\)**|Serializa una propiedad de imagen del tipo.|  
|**PX\_Short \(\)**|Serializa una propiedad de **corto** de tipo.|  
|**PX\_String \(\)**|Serializa una propiedad de `CString` de tipo.|  
|**PX\_ULong \(\)**|Serializan una propiedad de **ulong** de tipo.|  
|**PX\_UShort \(\)**|Serializan una propiedad de **ushort** de tipo.|  
  
 Para obtener más información sobre estas funciones de intercambio de propiedad, vea [Persistencia de controles OLE](../mfc/reference/persistence-of-ole-controls.md) en *la referencia de MFC*.  
  
##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> Personalizar el comportamiento predeterminado de DoPropExchange  
 La implementación predeterminada de **DoPropertyExchange** \(como se muestra en el tema anterior\) realiza una llamada a la clase base `COleControl`.  Esto serializa el conjunto de propiedades automáticamente admitidas por `COleControl`, que utiliza más espacio de almacenamiento que serializar solo las propiedades personalizadas del control.  Quitar esta llamada permite que el objeto serialice solo las propiedades que se considera importante.  Cualquier propiedad común indica el control ha implementado no será serializado al guardar o cargar el objeto de control a menos que se le agrega explícitamente las llamadas de **PX\_** para ellos.  
  
##  <a name="_core_implementing_version_support"></a> Implementar el control de versiones  
 Compatibilidad de versiones permite a un control ActiveX revisado para agregar nuevas propiedades persistentes y, aún puede detectar y cargar el estado persistente creada por una versión anterior del control.  Para crear la versión de un control disponibles como parte de los datos persistentes, llame a [COleControl::ExchangeVersion](../Topic/COleControl::ExchangeVersion.md) en función de `DoPropExchange` del control.  Esta llamada se insertará automáticamente si el control ActiveX se creó mediante el asistente para controles ActiveX.  Puede quitarse si la compatibilidad de versiones no es necesario.  Sin embargo, el costo de tamaño del control es muy pequeño \(4 bytes\) para la flexibilidad adicional de la compatibilidad con versión proporciona.  
  
 Si el control no se creó con el asistente para controles ActiveX, agregue una llamada a `COleControl::ExchangeVersion` insertando la línea siguiente al principio de la función de `DoPropExchange` \(antes de la llamada a `COleControl::DoPropExchange`\):  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_4.cpp)]  
  
 Puede utilizar cualquier `DWORD` como el número de versión.  Proyectos generados por el uso **\_wVerMinor** y **\_wVerMajor** del asistente para controles ActiveX como valor predeterminado.  Éstas son constantes globales definidas en el archivo de implementación de la clase de control ActiveX del proyecto.  En el resto de la función de `DoPropExchange` , puede llamar a [CPropExchange::GetVersion](../Topic/CPropExchange::GetVersion.md) en cualquier momento para recuperar la versión que va a guardar o que está recuperando.  
  
 En el ejemplo siguiente, la versión 1 de este control de ejemplo sólo tiene una propiedad de “ReleaseDate”.  La versión 2 agrega una propiedad “OriginalDate”.  Si el control se indica para cargar el estado persistente de la versión anterior, se inicializa la variable miembro para la nueva propiedad en un valor predeterminado.  
  
 [!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_5.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/CPP/mfc-activex-controls-serializing_4.cpp)]  
  
 De forma predeterminada, un control “convierte” datos anterior al último formato.  Por ejemplo, si la versión 2 de un control carga los datos que se guardó por la versión 1. escribirá el formato de la versión 2 cuando se guarda de nuevo.  Si desea que el control para guardar datos en la lectura del último de formato, pase **FALSE** como tercer parámetro al llamar a `ExchangeVersion`.  Este tercer parámetro es opcional y es **VERDADERO** de forma predeterminada.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)