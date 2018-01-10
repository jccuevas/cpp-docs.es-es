---
title: "Cómo: integrar herramientas personalizadas en las propiedades del proyecto | Documentos de Microsoft"
ms.custom: 
ms.date: 04/27/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.howto.integratecustomtools
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a762fc573953bcfb09180b9b830b761448d87a0d
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Cómo: Integrar herramientas personalizadas en las propiedades del proyecto
Puede agregar opciones de la herramienta personalizada a Visual Studio **páginas de propiedades** ventana mediante la creación de un archivo de esquema XML subyacente.  
  
 El **propiedades de configuración** sección de la **páginas de propiedades** ventana muestra los grupos de configuración que se conocen como *reglas*. Cada regla contiene la configuración de una herramienta o un grupo de funciones. Por ejemplo, el **vinculador** regla contiene la configuración de la herramienta del vinculador. La configuración de una regla puede dividirse en *categorías*.  
  
 Este documento explica cómo crear un archivo en un directorio de conjunto que contiene las propiedades de la herramienta personalizada para que las propiedades se cargan cuando se inicia Visual Studio. Para obtener información acerca de cómo modificar el archivo, consulte [plataforma Extensibilty parte 2](http://go.microsoft.com/fwlink/p/?linkid=191489) en el blog del equipo de proyecto de Visual Studio.  
  
### <a name="to-add-or-change-project-properties"></a>Para agregar o cambiar propiedades del proyecto  
  
1.  En el editor XML, cree un archivo XML.  
  
2.  Guarde el archivo en la Visual Studio de 2017 `VCTargets\1033` carpeta. Tendrá una ruta de acceso diferente para cada idioma y de cada edición de Visual Studio de 2017 que está instalado. Por ejemplo, la ruta de acceso de carpeta para la edición de Visual Studio Enterprise en inglés es `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. Ajustar la ruta de acceso para su idioma y la edición de Visual Studio. Cada regla en el **páginas de propiedades** ventana se representa mediante un archivo XML en esta carpeta. Asegúrese de que el archivo tiene un nombre exclusivo en la carpeta.  
  
3.  Copie el contenido del `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`, ciérrelo sin guardar los cambios y, a continuación, pegue el contenido en el nuevo archivo XML. Puede utilizar cualquier archivo de esquema XML: Esto es solo una que se puede usar para empezar con una plantilla.  
  
4.  En el nuevo archivo XML, modifique el contenido según sus requisitos. Asegúrese de cambiar el **nombre de la regla** y **Rule.DisplayName** en la parte superior del archivo.  
  
5.  Guarde los cambios y cierre el archivo.  
  
6.  Archivos XML en `%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` se cargan cuando se inicia Visual Studio. Por lo tanto, para probar el nuevo archivo, reinicie Visual Studio.  
  
7.  En **el Explorador de soluciones**, haga clic en un proyecto y, a continuación, haga clic en **propiedades**. En el **páginas de propiedades** ventana, en el panel izquierdo, compruebe que hay un nuevo nodo con el nombre de la regla.  
  
## <a name="see-also"></a>Vea también  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
