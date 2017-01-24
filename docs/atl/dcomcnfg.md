---
title: "DCOMCNFG | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DCOMCNFG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DCOM, configuring in ATL"
  - "DCOMCNFG utility"
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DCOMCNFG
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**DCOMCNFG** es una utilidad de Windows NT 4.0 que permite configurar valores diferentes DCOM\- específicos en el registro.  La ventana de **DCOMCNFG** tiene tres páginas: seguridad predeterminada, propiedades predeterminadas, y aplicaciones.  En Windows 2000 una cuarta página, protocolos predeterminados, está presente.  
  
## Página Seguridad predeterminada  
 Puede utilizar la página Seguridad predeterminada para especificar los permisos predeterminados para los objetos del sistema.  La página Seguridad predeterminada tiene tres secciones: Access, inicio, y configuración.  Para cambiar los valores predeterminados de una sección, haga clic en el botón correspondiente de **Editar valores predeterminados** .  Esta configuración de seguridad predeterminada se almacena en el registro con `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`.  
  
## Página predeterminada de los protocolos  
 Esta página enumera el conjunto de protocolos de red disponibles a DCOM en este equipo.  El orden refleja la prioridad en la que se utilizarán; el primero de la lista tiene la prioridad máxima.  Los protocolos se pueden agregar o eliminar de esta página.  
  
## Página de propiedades predeterminadas  
 En la página de propiedades predeterminada, debe activar la casilla de **Habilitar COM distribuido en este equipo** si desea que los clientes en otros equipos para tener acceso a los objetos COM que se ejecutan en este equipo.  La selección esta las opciones establecidas `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` valora a `Y`.  
  
## Página de aplicaciones  
 Cambia los valores para un objeto determinado con la página de aplicaciones.  Seleccionar la aplicación de la lista y haga clic en el botón de **Propiedades** .  La ventana Propiedades tiene cinco páginas:  
  
-   La página general confirma la aplicación que está trabajando.  
  
-   La página de ubicación permite especificar que la aplicación se debe ejecutar cuando un cliente llama a `CoCreateInstance` en CLSID pertinente.  Si activa la casilla de **Ejecutar la aplicación en el siguiente equipo** y especifica un nombre de equipo, un valor de `RemoteServerName` se agrega en el AppID para esa aplicación.  Desactivar la casilla de **Run application on this computer** cambia el valor de `LocalService` a `_LocalService` y, de esta manera, la deshabilita.  
  
-   La página Seguridad es similar a la página Seguridad predeterminada encontrada en la ventana de **DCOMCNFG** , salvo que esta configuración se aplica únicamente a la aplicación actual.  Una vez más los valores se almacenan bajo el AppID para ese objeto.  
  
-   La página test identifica utilizan a qué usuario para ejecutar la aplicación.  
  
-   La página de los extremos enumera el conjunto de protocolos y de extremos disponibles para uso de clientes del servidor seleccionado DCOM.  
  
## Vea también  
 [Servicios](../atl/atl-services.md)