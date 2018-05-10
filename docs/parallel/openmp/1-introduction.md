---
title: 1. Introducción | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 883af9cb48a0fb13dbb9a758d6f8174096d4c0c3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="1-introduction"></a>1. Introducción
Este documento especifica una colección de directivas de compilador, funciones de la biblioteca y las variables de entorno que pueden utilizarse para especificar el paralelismo de memoria compartida en programas de C y C++. La funcionalidad descrita en este documento se conoce colectivamente como la *interfaz de programación de aplicaciones (API) de OpenMP C/C++*. El objetivo de esta especificación es proporcionar un modelo de programación en paralelo que permite que un programa como portables entre arquitecturas de memoria compartida de diferentes proveedores. La API de C/C++ de OpenMP se admitirán los compiladores de muchos proveedores. Para obtener más información acerca de OpenMP, incluido el *interfaz de programación de aplicaciones de OpenMP Fortran*, puede encontrarse en el siguiente sitio web:  
  
 [http://www.openmp.org](http://www.openmp.org)  
  
 Las directivas, funciones de la biblioteca y las variables de entorno definidas en este documento le permitirá a los usuarios crear y administrar programas paralelos al permitir la portabilidad. Las directivas de amplían la C y la programación de C++ secuencial modelo con el único programa varias estructuras de datos (SPMD), construcciones de uso compartido y las construcciones de sincronización y proporcionan soporte técnico para el uso compartido y privatization de datos. Los compiladores que admiten OpenMP C y C++ API incluirá una opción de línea de comandos para el compilador que activa y permite la interpretación de todas las directivas de compilador de OpenMP.