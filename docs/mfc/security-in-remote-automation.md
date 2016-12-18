---
title: "Seguridad de la automatizaci&#243;n remota | Microsoft Docs"
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
  - "activar objetos"
  - "AllowRemoteActivation"
  - "objetos de automatización, opciones de seguridad"
  - "activación de objetos"
  - "automatización remota, seguridad"
  - "seguridad [MFC]"
  - "seguridad [MFC], automatización remota"
ms.assetid: 276b300d-c0b5-4bd8-8bf5-0270994b9cfa
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Seguridad de la automatizaci&#243;n remota
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La automatización remota admite un nivel de seguridad básico permite que un programador de la aplicación de servidor \(o, en su lugar, el administrador\) especifica cómo un objeto concreto se puede provocar remotamente.  Todos los objetos de automatización en un sistema determinado se pueden global establecer “denegar la activación remota” o “permite la activación remota”.  Además, y más a menudo, los objetos individuales se pueden dar tales funciones.  La automatización remota utiliza una clave en los valores del registro de cada objeto, **AllowRemoteActivation**, para determinar si un servidor determinado puede activarse de forma remota.  Si para todo el sistema los valores utilizan este modo, cada objeto del registro pueden asignar esta clave, y el estado de cada uno puede establecer “sí” o “no” según corresponda.  
  
 Si el sistema del servidor está ejecutando Windows NT o Windows 2000, un formulario alternativo de seguridad se permite.  En este caso, la automatización remota usa la lista de control de acceso \(ACL\) NT para especificar los usuarios o el grupo o grupos de usuarios pueden remotamente provocar un servidor determinado.  
  
 Observe que las opciones de seguridad se aplican al objeto de conjunto; no es posible establecer atributos de una interfaz específica, o propiedades individuales o métodos en el objeto.  
  
 Todas las opciones de seguridad se pueden establecer a través del administrador de Conexión \(RAC\) de automatización remota.  
  
## Vea también  
 [Automatización remota](../mfc/remote-automation.md)