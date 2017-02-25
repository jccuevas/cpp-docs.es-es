---
title: "Redistribuir archivos de compatibilidad con bases de datos | Microsoft Docs"
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
  - "archivos de compatibilidad con bases de datos [C++], redistribuir"
  - "redistribuir archivos de compatibilidad con bases de datos"
ms.assetid: d80cffe0-177c-4515-9de7-fbf0517eb8d6
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# Redistribuir archivos de compatibilidad con bases de datos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede redistribuir archivos de compatibilidad para objetos de acceso a datos \(DAO\) y para las tecnologías de base de datos en el Kit de desarrollo de software \(SDK\) de Microsoft Data Access.  
  
## Instalar archivos de compatibilidad DAO  
 Para obtener la versión más reciente de DAO, vea el [artículo 239114: Cómo obtener el Service Pack más reciente para el motor de base de datos Microsoft Jet 4.0](http://go.microsoft.com/fwlink/?LinkId=198014) en el sitio web de Soporte de Microsoft.  
  
## Instalar los archivos de compatibilidad del Microsoft Data Access SDK  
 Use Mdac\_typ.exe para instalar los archivos de compatibilidad con ODBC, OLE DB, ActiveX Data Objects \(ADO\) y Remote Data Services \(RDS\).  Mdac\_typ.exe se encuentra en la carpeta ..\\WCU\\MDAC28\\ del disco de instalación de Visual Studio.  También puede descargar Mdac\_typ.exe desde el sitio web [Centro de descarga de Microsoft](http://go.microsoft.com/fwlink/?LinkId=198015).  
  
 Para obtener más información, en el sitio web de [MSDN](http://go.microsoft.com/fwlink/?LinkId=198016), busque “Redistribuir MDAC 2.8 SP1”.  Si utiliza los proyectos de instalación de Visual Studio para implementar la aplicación, vea [Deployment and Dependencies](http://msdn.microsoft.com/es-es/49e9b84d-bd6a-4388-b9ac-46ea79cf0733).  
  
## Vea también  
 [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md)