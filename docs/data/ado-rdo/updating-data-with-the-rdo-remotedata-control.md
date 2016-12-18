---
title: "Actualizar datos con el control RemoteData de RDO | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RemoteData (control de RDO)"
  - "RemoteData (control de RDO), actualizar datos"
  - "RemoteData (control)"
  - "RemoteData (control), actualizar datos"
ms.assetid: abb4175f-612e-4645-905e-c0fa918b0fd7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Actualizar datos con el control RemoteData de RDO
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los datos del control RemoteData de RDO pueden ser de sólo lectura o modificables.  
  
### Para crear una aplicación que modifique datos mediante el control RemoteData de RDO  
  
1.  Establezca el valor de la propiedad **CursorDriver** del control RemoteData de RDO.  
  
    -   Los cursores del lado del servidor almacenan los datos devueltos en el servidor.  
  
    -   Los cursores del lado del cliente ODBC almacenan datos en el almacenamiento local del cliente.  
  
    -   Los cursores por lotes del lado del cliente utilizan una biblioteca de cursores para tratar problemas de simultaneidad.  
  
    -   No se utiliza ninguna opción Cursor cuando se realiza una consulta de acción y, por tanto, no es necesario ningún cursor.  
  
2.  Establezca el valor de la propiedad **LockType** del control RemoteData de RDO.  Se recomienda la opción de utilizar simultaneidad optimista basada en el conjunto de resultados.  
  
    -   No se debe utilizar la simultaneidad de sólo lectura si se desea poder modificar los datos.  
  
    -   La simultaneidad pesimista bloquea los datos durante la actualización de forma que no existe el riesgo de que otros usuarios confirmen cambios incompatibles de los datos.  
  
    -   La simultaneidad optimista no bloquea los datos pero si detecta durante el proceso de confirmación que el cliente ha publicado un estado incompatible, el control RemoteData de RDO produce un error.  
  
3.  Establezca el valor de la propiedad **ResultsetType** del control RemoteData de RDO.  Compruebe que el controlador ODBC admite las opciones elegidas:  
  
    -   Cuando se elige Crear cursor estático, no se detectarán los cambios hasta que se cierre el cursor y se vuelva a abrir.  
  
    -   Si se elige Crear cursor de conjunto de claves, el cursor permitirá insertar, actualizar y eliminar cuando lo desee, dentro del mismo cursor de conjunto de claves.  
  
4.  Configure el control enlazado a datos como sea necesario para permitir las actualizaciones.  Tenga en cuenta que algunos controles no permiten la actualización.  
  
 Para obtener información sobre cómo utilizar estos objetos, consulte la documentación sobre el control RemoteData de RDO.  
  
## Vea también  
 [Enlace de datos de RDO](../../data/ado-rdo/rdo-databinding.md)   
 [Utilizar el enlace de datos de RDO en Visual C\+\+](../../data/ado-rdo/using-rdo-databinding-in-visual-cpp.md)