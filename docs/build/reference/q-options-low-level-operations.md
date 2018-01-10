---
title: Opciones -Q (operaciones de bajo nivel) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /q
dev_langs: C++
helpviewer_keywords:
- Q compiler option [C++]
- -Q compiler option [C++]
- /Q compiler option [C++]
ms.assetid: 9fa738b9-630a-4bde-bc87-bdfa30552be4
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d970c2de5e34840ab2ed77f229c329db3c6f72fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="q-options-low-level-operations"></a>/Q (Opciones) (Operaciones de bajo nivel)
Puede usar el **/q** opciones del compilador para realizar las siguientes operaciones de compilador de bajo nivel:  
  
-   [/ Qfast_transcendentals (Force funciones transcendentales rápidas)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): genera funciones transcendentales rápidas.  
  
-   [/QIfist (suprimir _ftol)](../../build/reference/qifist-suppress-ftol.md): suprime `_ftol` cuando una conversión de un tipo de punto flotante a un tipo entero es necesaria (sólo x86).  
  
-   [/ Qimprecise_fwaits (quitar comandos fwait en los bloques Try)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): quita `fwait` comandos dentro de `try` bloques.  
  
-   [/Qpar (Paralelizador automático)](../../build/reference/qpar-auto-parallelizer.md): habilita la paralelización automática de bucles marcados con el [#pragma loop()](../../preprocessor/loop.md) directiva.  
  
-   [/ Qpar-report (nivel de información de Paralelizador automático)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): habilita los niveles de ejecución en paralelo automática de informe.  
  
-   [/ Qsafe_fp_loads](../../build/reference/qsafe-fp-loads.md): suprime las optimizaciones de registro de punto flotante carga y para mover entre la memoria y MMX registra.  
  
-   [/ Qvec-report (nivel de información de Vectorizador automático)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): permite niveles de informe para la vectorización automática.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)