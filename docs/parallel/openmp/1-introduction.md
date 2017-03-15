---
title: "1. Introduction | Microsoft Docs"
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
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 1. Introduction
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este documento especifica una colección de directivas del compilador, funciones de biblioteca, y variables de entorno que se pueden utilizar para especificar el paralelismo de memoria compartida en programas de c y C\+\+.  La funcionalidad descrita en este documento se conocen colectivamente como *la interfaz de programación de aplicaciones de OpenMP C\/C\+\+ \(API\)*.  El objetivo de esta especificación es proporcionar un modelo para la programación paralela que permite que un programa sea portable a través de las arquitecturas de memoria compartida de proveedores diferentes.  El OpenMP C\/C\+\+ API se compatibles los compiladores de proveedores numerosos.  Más información sobre OpenMP, incluida *la interfaz de programación de aplicaciones de FORTRAN de OpenMP*, se puede encontrar en el siguiente sitio Web:  
  
 [http:\/\/www.openmp.org](http://www.openmp.org)  
  
 Las directivas, funciones de biblioteca, y las variables de entorno definido en este documento permitirá a los usuarios crear y administrar programas paralelos mientras permiten portabilidad.  Las directivas extienden el modelo de programación secuencial de c y C\+\+ con las estructuras de datos de un único \(SPMD\) programa, las construcciones de división del trabajo, y las construcciones de sincronización, y proporcionan compatibilidad para el uso compartido y la privatización de datos.  Los compiladores que admiten el OpenMP C y C\+\+ API tendrán una opción de la línea de comandos al compilador que genera y permite la interpretación de todas las directivas de compilador de OpenMP.