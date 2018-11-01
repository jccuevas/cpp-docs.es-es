---
title: 1. Introducción
ms.date: 11/04/2016
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: b365ff828fd7dc2b7d9d3136a4fbfb68c43902ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554718"
---
# <a name="1-introduction"></a>1. Introducción

Este documento especifica una colección de directivas de compilador, las funciones de biblioteca y las variables de entorno que pueden utilizarse para especificar el paralelismo de memoria compartida en los programas C y C++. La funcionalidad descrita en este documento se conoce colectivamente como la *interfaz de programa de aplicaciones (API) de OpenMP C/C ++*. El objetivo de esta especificación es proporcionar un modelo de programación en paralelo que permite que un programa sea portable entre arquitecturas de memoria compartida de diferentes proveedores. La API de C/C ++ OpenMP se admitirán los compiladores de muchos proveedores. Para obtener más información acerca de OpenMP, incluido el *interfaz de programación de aplicaciones de OpenMP Fortran*, puede encontrarse en el siguiente sitio web:

[http://www.openmp.org](http://www.openmp.org)

Las directivas, las funciones de biblioteca y variables de entorno definidas en este documento, permitirá a los usuarios crear y administrar programas paralelos al tiempo que permite la portabilidad. Las directivas de amplían la C y la programación secuencial de C++ de modelo con el único programa varias construcciones de datos (SPMD), las construcciones de uso compartido y construcciones de sincronización y proporcionan soporte para el uso compartido y privatización en modo de datos. Los compiladores que admiten la de OpenMP C y C++ API incluirá una opción de línea de comandos al compilador que se activa y permite la interpretación de todas las directivas de compilador de OpenMP.