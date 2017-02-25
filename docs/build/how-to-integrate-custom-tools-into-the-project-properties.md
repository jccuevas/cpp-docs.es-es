---
title: "C&#243;mo: Integrar herramientas personalizadas en las propiedades del proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.howto.integratecustomtools"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (C++), cómo: integrar herramientas personalizadas"
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Integrar herramientas personalizadas en las propiedades del proyecto
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede agregar opciones personalizadas de la herramienta a la ventana de Visual Studio **Páginas de propiedades** creando un archivo de esquema XML subyacente.  
  
 La sección **Propiedades de configuración** de la ventana **Páginas de propiedades** muestra los grupos de configuraciones que se conocen como *reglas*.  Cada regla contiene la configuración para una herramienta o un grupo de características.  Por ejemplo, la regla de **Vinculador** contiene la configuración para la herramienta del vinculador.  Los valores en una regla se pueden subdividir en *categorías*.  
  
 En este documento se explica cómo crear un archivo en un directorio del conjunto que contiene las propiedades para la herramienta personalizada de forma que se cargan las propiedades cuando Visual Studio se inicia.  Para obtener información sobre cómo modificar el archivo, vea [Parte 2 de Extensibilty de la plataforma](http://go.microsoft.com/fwlink/?LinkID=191489) en el blog del equipo de proyecto de Visual Studio.  
  
### Para agregar o cambiar las propiedades del proyecto  
  
1.  En el Editor XML, cree un archivo XML.  
  
2.  Guarde el archivo en la carpeta %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\.  Cada regla en la ventana **Páginas de propiedades** se representa mediante un archivo XML en esta carpeta.  Asegúrese de que el archivo tiene nombre único en la carpeta.  
  
3.  Copie el contenido de %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\cl.xml, ciérrelo sin guardar los cambios y, a continuación, pegue el contenido en el nuevo archivo XML.  Puede utilizar cualquier archivo de esquema XML: éste es el único que puede usarse para comenzar con una plantilla.  
  
4.  En el nuevo archivo XML, modifique el contenido según sus requisitos.  Asegúrese de cambiar el **nombre de la regla**, así como **Rule.DisplayName**, en la parte superior del archivo.  
  
5.  Guarde los cambios y cierre el archivo.  
  
6.  Los archivos XML en %ProgramFiles%\\MSBuild\\Microsoft.Cpp\\v4.0\\ se cargan cuando se inicia Visual Studio.  Por consiguiente, para probar el nuevo archivo, reinicie Visual Studio.  
  
7.  En el **Explorador de soluciones**, haga clic con el botón secundario en un proyecto y, a continuación, seleccione **Propiedades**.  En la ventana **Páginas de propiedades**, en el panel de la izquierda, compruebe que hay un nuevo nodo con el nombre de la regla.  
  
## Vea también  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)