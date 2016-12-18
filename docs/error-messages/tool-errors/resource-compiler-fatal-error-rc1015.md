---
title: "Error irrecuperable del compilador de recursos RC1015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC1015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1015"
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable del compilador de recursos RC1015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede abrir el archivo de inclusión 'nombredearchivo'  
  
 El archivo de inclusión dado no existe, no se pudo abrir o no se encontró.  
  
 Asegúrese de que sea válida la configuración de entorno y de que se haya especificado la ruta de acceso correcta para el archivo.  Asegúrese de que estén disponibles suficientes identificadores de archivo para el compilador de recursos.  Si el archivo está en una unidad de red, asegúrese de tener permisos para abrir el archivo.  
  
 R C1015 puede producirse aunque el archivo de inclusión existe en un directorio especificado como directorio de inclusión adicional en las propiedades de configuración \-\> recursos \(\> página de propiedades General; especifique la ruta completa al archivo de inclusión.  
  
 Para obtener más información, vea el artículo Q326987 de Knowledge Base: RC1015 Error When Using Resource View If the Include Path is Too Long.