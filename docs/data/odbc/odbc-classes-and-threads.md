---
title: "Clases y subprocesos de ODBC | Microsoft Docs"
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
  - "clases ODBC, subprocesos"
  - "ODBC, aplicaciones multiproceso"
  - "subprocesamiento [MFC], compatibilidad con ODBC"
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases y subprocesos de ODBC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Empezando por MFC 4.2, hay una compatibilidad con multithreading para las clases ODBC de MFC.  Sin embargo, hay que tener en cuenta que MFC no admite el multithreading para las clases DAO.  
  
 La compatibilidad con el multithreading para las clases ODBC tiene algunas limitaciones.  Como estas clases se ajustan a la API de ODBC, están limitadas a la compatibilidad con multithreading de los componentes en los que están integradas.  Por ejemplo, muchos controladores ODBC no funcionan correctamente con subprocesos; por ello, las clases ODBC de MFC no funcionan correctamente con subprocesos si se utilizan con uno de estos controladores.  Se debe comprobar si el controlador en cuestión funciona correctamente con subprocesos.  
  
 Cuando se crea una aplicación multiproceso, hay que tener mucho cuidado al utilizar varios subprocesos para manipular el mismo objeto.  Por ejemplo, si se utiliza el mismo objeto `CRecordset` en dos subprocesos, pueden surgir problemas a la hora de recuperar datos; una operación de obtención en un subproceso puede sobrescribir los datos obtenidos en el otro subproceso.  Un uso más corriente de las clases ODBC de MFC en subprocesos independientes consiste en compartir un objeto `CDatabase` abierto entre varios subprocesos para utilizar la misma conexión ODBC, con un objeto `CRecordset` independiente en cada subproceso.  Conviene señalar que no se debe pasar un objeto `CDatabase` no abierto a un objeto `CRecordset` en otro subproceso.  
  
> [!NOTE]
>  Si es necesario tener varios subprocesos para manipular el mismo objeto, se deben implementar los mecanismos de sincronización apropiados, como, por ejemplo, secciones críticas.  Hay que tener presente que ciertas operaciones, como **Abrir**, no están protegidas.  Conviene asegurarse de que no se llame a estas operaciones simultáneamente desde subprocesos independientes.  
  
 Para obtener más información acerca de la creación de aplicaciones multiproceso, vea [Temas de multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
## Vea también  
 [Conectividad abierta de bases de datos \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Programación del acceso a datos \(MFC\/ATL\)](../../data/data-access-programming-mfc-atl.md)