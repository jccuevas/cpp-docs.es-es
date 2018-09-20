---
title: 1. Introducción | Microsoft Docs
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
ms.openlocfilehash: 4ce963d312d145e26567a5902f32e45735eb1d89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438423"
---
# <a name="1-introduction"></a>1. Introducción

Este documento especifica una colección de directivas de compilador, las funciones de biblioteca y las variables de entorno que pueden utilizarse para especificar el paralelismo de memoria compartida en los programas C y C++. La funcionalidad descrita en este documento se conoce colectivamente como la *interfaz de programa de aplicaciones (API) de OpenMP C/C ++*. El objetivo de esta especificación es proporcionar un modelo de programación en paralelo que permite que un programa sea portable entre arquitecturas de memoria compartida de diferentes proveedores. La API de C/C ++ OpenMP se admitirán los compiladores de muchos proveedores. Para obtener más información acerca de OpenMP, incluido el *interfaz de programación de aplicaciones de OpenMP Fortran*, puede encontrarse en el siguiente sitio web:

[http://www.openmp.org](http://www.openmp.org)

Las directivas, las funciones de biblioteca y variables de entorno definidas en este documento, permitirá a los usuarios crear y administrar programas paralelos al tiempo que permite la portabilidad. Las directivas de amplían la C y la programación secuencial de C++ de modelo con el único programa varias construcciones de datos (SPMD), las construcciones de uso compartido y construcciones de sincronización y proporcionan soporte para el uso compartido y privatización en modo de datos. Los compiladores que admiten la de OpenMP C y C++ API incluirá una opción de línea de comandos al compilador que se activa y permite la interpretación de todas las directivas de compilador de OpenMP.