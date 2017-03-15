---
title: "Documentaci&#243;n XML (Visual C++) | Microsoft Docs"
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
  - "/// (delimitador para documentación en C++)"
  - "comentarios, archivos de código fuente de C++"
  - "documentación XML"
  - "XML, comentarios de documentación en código fuente"
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Documentaci&#243;n XML (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En Visual C\+\+, puede agregar comentarios al código fuente que se procesará un archivo .xml.  Este archivo puede ser la entrada a un proceso que cree la documentación para las clases del código.  
  
 En un archivo de código de Visual C\+\+, los Comentarios de documentación XML se deben encontrar directamente antes de un método o definición de tipo.  Los comentarios se pueden usar para rellenar la sugerencia de datos Intellisense QuickInfo en los escenarios siguientes:  
  
1.  cuando el código se compila como un componente en tiempo de ejecución de Windows con un archivo de acompañamiento de .winmd  
  
2.  cuando el código fuente se incluye en el proyecto actual  
  
3.  en una biblioteca cuyas declaraciones e implementaciones se encuentran en el mismo archivo de encabezado  
  
> [!NOTE]
>  En la versión actual, los comentarios de código no se procesan en plantillas o nada que contiene un tipo de plantilla \(por ejemplo, una función que toma un parámetro como plantilla\).  Agregar estos comentarios dará lugar a un comportamiento indefinido.  
  
 Para obtener información sobre cómo crear un archivo .xml con comentarios de documentación, vea los temas siguientes.  
  
|Para obtener más información sobre|Vea|  
|----------------------------------------|---------|  
|Las opciones del compilador para usar|[\/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
|Etiquetas que puede utilizar para proporcionar funcionalidad de uso frecuente en la documentación|[Etiquetas recomendadas para comentarios de documentación](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|  
|Las cadenas de identificación que el compilador genera para identificar las construcciones del código|[Procesar el archivo .xml](../ide/dot-xml-file-processing.md)|  
|Cómo delimitar etiquetas de la documentación|[Delimitadores para las etiquetas de la documentación de Visual C\+\+](../ide/delimiters-for-visual-cpp-documentation-tags.md)|  
|Generar un archivo .xml de uno o más archivos .xdc.|[Referencia de XDCMake](../ide/xdcmake-reference.md)|  
|Vínculos a información sobre XML respecto a las áreas de características de Visual Studio|[XML en Visual Studio](../Topic/XML%20Tools%20in%20Visual%20Studio.md)|  
  
 Si tiene que colocar los caracteres especiales XML en el texto de un comentario de documentación, debe utilizar entidades XML o sección CDATA.  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)