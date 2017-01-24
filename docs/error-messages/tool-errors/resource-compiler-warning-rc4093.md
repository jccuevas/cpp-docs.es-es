---
title: "Advertencia del compilador de recursos RC4093 | Microsoft Docs"
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
  - "RC4093"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4093"
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador de recursos RC4093
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

nueva línea sin escape en una constante de caracteres del código inactivo  
  
 La expresión constante de una directiva de preprocesador `#if`, `#elif`, **\#ifdef** o **\#ifndef** evaluada a cero provoca que el código que sigue esté inactivo.  Dentro del código inactivo, un carácter de nueva línea ha aparecido dentro de un juego de signos de comillas sencillas o tipográficas.  
  
 Todo el texto hasta el siguiente signo de comillas tipográficas se ha considerado dentro de una constante de caracteres.