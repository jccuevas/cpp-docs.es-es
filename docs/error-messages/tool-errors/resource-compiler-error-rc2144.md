---
title: "Error del compilador de recursos RC2144 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2144"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2144"
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador de recursos RC2144
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El ID. DE IDIOMA PRINCIPAL no es un número  
  
 El ID. DE IDIOMA PRINCIPAL debe ser un identificador en lenguaje hexadecimal.  Consulte [Cadenas de idioma y de país o región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) en la *Referencia de la biblioteca en tiempo de ejecución* para obtener una lista de identificadores de idioma válidos.  
  
 Este error también puede producirse si los recursos se han agregado y eliminado del archivo .RC utilizando una herramienta.  Para corregir este problema, abra el archivo .RC en un editor de texto y limpie manualmente los recursos no utilizados.