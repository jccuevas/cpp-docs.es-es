---
title: "Archivos .Ilk como entrada del vinculador | Microsoft Docs"
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
  - ".ilk (archivos)"
  - "ILK (archivos)"
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos .Ilk como entrada del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Al vincular de forma incremental, LINK actualiza el archivo de estado .ilk que crea en la primera vinculación incremental.  Este archivo tiene el mismo nombre base que el archivo .exe o .dll y su extensión es .ilk.  Durante vinculaciones incrementales posteriores, LINK actualiza el archivo .ilk.  Si falta el archivo .ilk, LINK ejecuta un vínculo completo y crea un archivo .ilk nuevo.  Si este archivo no puede utilizarse, LINK ejecutará una vinculación no incremental.  Para obtener más detalles acerca de la vinculación incremental, vea la opción [\/INCREMENTAL \(Vincular de forma incremental\)](../../build/reference/incremental-link-incrementally.md).  
  
## Vea también  
 [Archivos de entrada de LINK](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)