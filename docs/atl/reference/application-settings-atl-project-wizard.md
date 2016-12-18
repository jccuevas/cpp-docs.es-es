---
title: "Configuraci&#243;n de la aplicaci&#243;n, Asistente para proyectos ATL | Microsoft Docs"
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
  - "vc.appwiz.atl.com.appset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para proyectos ATL, configuración de la aplicación"
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
caps.latest.revision: 17
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Configuraci&#243;n de la aplicaci&#243;n, Asistente para proyectos ATL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice la página **Configuración de la aplicación** del Asistente para proyectos ATL, para diseñar y agregar características básicas a un nuevo proyecto ATL.  
  
## Tipo de servidor  
 Elija uno de los tres tipos de servidor posibles:  
  
 **Biblioteca de vínculos dinámicos \(DLL\)**  
 Seleccione crear un servidor en proceso.  
  
 **Ejecutable \(EXE\)**  
 Seleccione crear un servidor local fuera de proceso.  Esta opción no permite compatibilidad con MFC ni COM\+ 1.0.  No permite la combinación de código auxiliar y proxy.  
  
 **Servicio \(EXE\)**  
 Seleccione crear una aplicación para Windows que se ejecute en segundo plano cuando se inicie Windows.  Esta opción no permite la compatibilidad con MFC ni COM\+ 1.0 ni permite combinar código proxy y código auxiliar.  
  
## Opciones adicionales  
  
> [!NOTE]
>  Todas las opciones adicionales sólo están disponibles para proyectos de archivo DLL.  
  
 **Permitir la combinación de código auxiliar y proxy**  
 Active la casilla **Permitir la combinación de código auxiliar y proxy** por comodidad cuando sea necesario el cálculo de referencias de interfaces.  Esta opción coloca el código proxy y el código auxiliar generados por MIDL en el mismo ejecutable que el servidor.  
  
 **Dirección MFC de soporte**  
 Seleccione esta opción si desea especificar que el objeto debe incluir compatibilidad con MFC.  Esta opción vincula el proyecto a las bibliotecas MFC de forma que pueda tener acceso a cualquiera de las clases y funciones que contienen.  
  
 **Compatibilidad con COM\+ 1.0**  
 Seleccione esta opción para modificar la configuración a fin de compilar el proyecto de forma que admita componentes de COM\+ 1.0.  Además de la lista estándar de bibliotecas, el asistente agrega la biblioteca específica de componentes COM\+ 1.0, comsvcs.lib.  
  
 Además, el archivo mtxex.dll se carga con retraso en el sistema host cuando se inicia la aplicación.  
  
-   **Registrador de componentes admiten** Si el proyecto ATL contiene soporte para COM\+ 1,0 componentes, puede establecer esta opción.  El registrador de componentes permite al objeto COM\+ 1.0 obtener una lista de componentes, registrar componentes o eliminar componentes del registro \(individualmente o todos a la vez\).  
  
## Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)   
 [Configuraciones predeterminadas de un proyecto ATL](../../atl/reference/default-atl-project-configurations.md)