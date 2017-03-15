---
title: "Implementaci&#243;n en Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "implementación de aplicaciones [C++]"
  - "implementar aplicaciones [C++]"
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Implementaci&#243;n en Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al implementar una aplicación de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] en otro equipo, debe instalar tanto la aplicación como todos los archivos de biblioteca de los que depende.  Si se actualiza una biblioteca \(por ejemplo, cuando se corrige una vulnerabilidad de seguridad\), probablemente deseará aplicar la actualización siempre que se implemente la aplicación.  
  
 Visual Studio ofrece tres maneras de implementar las bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] junto con la aplicación: implementación central, implementación local y vinculación estática.  Microsoft actualiza automáticamente sus bibliotecas que se implementan centralmente.  En el caso de las bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] que se implementan localmente o se vinculan estáticamente, el autor de la aplicación debe proporcionar las actualizaciones.  
  
## Implementación central  
 En la implementación central, los archivos de biblioteca de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] se instalan en el directorio %windir%\\system32\\.  Para implementar centralmente las bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)], puede usar uno de los elementos siguientes:  
  
-   *Archivos de paquete redistribuible*, que son archivos ejecutables independientes de la línea de comandos que puede usar para instalar las bibliotecas redistribuibles de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)].  
  
-   *Módulos de combinación redistribuibles \(archivos .msm\)*, que puede emplear para implementar determinadas bibliotecas y que incluye en el archivo de Windows Installer \(.msi\) de la aplicación.  
  
 Un archivo de paquete redistribuible instala las bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] para una arquitectura del sistema concreta.  Se puede programar la instalación de la aplicación para que se ejecute como un requisito previo antes de instalar la aplicación.  Un módulo de combinación permite incluir lógica de instalación para una biblioteca concreta de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] en un archivo de instalación de la aplicación de Windows Installer.  Se pueden incluir tantos módulos de combinación como necesite la aplicación.  
  
 Puesto que la implementación central de bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] mediante un paquete redistribuible habilita la actualización automática por parte de Microsoft, se recomienda usar la vinculación dinámica y paquetes redistribuibles para la aplicación.  
  
## Implementación local  
 En la implementación local, archivos de biblioteca se instalan en la carpeta de la aplicación junto con el archivo ejecutable.  Se pueden instalar versiones diferentes de las bibliotecas en la misma carpeta porque el nombre de archivo de cada versión se crea de forma única con la inclusión de su número de versión.  Por ejemplo, la versión 12 del runtime de C es msvcr120.dll.  
  
 Como Microsoft no puede actualizar automáticamente las bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] implementadas localmente, hay que tener cuidado con la implementación local de estas bibliotecas.  Si decide usar la implementación local de bibliotecas redistribuibles, se recomienda que implemente su propio método de actualizar automáticamente las bibliotecas implementadas localmente.  
  
## Vinculación estática  
 Puede vincular estáticamente una biblioteca de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] a una aplicación \(es decir, compilarla en la aplicación\) de modo que no tenga que implementar los archivos de biblioteca de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] por separado.  Sin embargo, tenga cuidado con este enfoque porque las bibliotecas vinculadas estáticamente no se pueden actualizar en contexto.  Si usa la vinculación estática y desea actualizar una biblioteca vinculada, tiene que recompilar y volver a implementar la aplicación.  
  
## Solución de problemas  
 El orden de carga de las bibliotecas de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] depende del sistema.  Para diagnosticar los problemas de cargador, utilice depends.exe o where.exe.  Para obtener más información, vea el tema sobre el [orden de búsqueda de las bibliotecas de vínculos dinámicos \(Windows\)](http://msdn.microsoft.com/library/windows/desktop/ms682586.aspx).  
  
## Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)