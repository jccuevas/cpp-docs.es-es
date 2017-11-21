---
title: "1. Introducción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 766ab1b367cd3d13f26243a68caf5c207069dd4c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="1-introduction"></a>1. Introducción
Este documento especifica una colección de directivas de compilador, funciones de la biblioteca y las variables de entorno que pueden utilizarse para especificar el paralelismo de memoria compartida en programas de C y C++. La funcionalidad descrita en este documento se conoce colectivamente como la *interfaz de programación de aplicaciones (API) de OpenMP C/C++*. El objetivo de esta especificación es proporcionar un modelo de programación en paralelo que permite que un programa como portables entre arquitecturas de memoria compartida de diferentes proveedores. La API de C/C++ de OpenMP se admitirán los compiladores de muchos proveedores. Para obtener más información acerca de OpenMP, incluido el *interfaz de programación de aplicaciones de OpenMP Fortran*, puede encontrarse en el siguiente sitio web:  
  
 [http://www.OpenMP.org](http://www.openmp.org)  
  
 Las directivas, funciones de la biblioteca y las variables de entorno definidas en este documento le permitirá a los usuarios crear y administrar programas paralelos al permitir la portabilidad. Las directivas de amplían la C y la programación de C++ secuencial modelo con el único programa varias estructuras de datos (SPMD), construcciones de uso compartido y las construcciones de sincronización y proporcionan soporte técnico para el uso compartido y privatization de datos. Los compiladores que admiten OpenMP C y C++ API incluirá una opción de línea de comandos para el compilador que activa y permite la interpretación de todas las directivas de compilador de OpenMP.