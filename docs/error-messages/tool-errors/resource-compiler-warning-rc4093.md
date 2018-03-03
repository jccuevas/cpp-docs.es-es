---
title: Advertencia del compilador de recursos RC4093 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC4093
dev_langs:
- C++
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d21cbba379e72675b8957be58dc712b83673947
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-warning-rc4093"></a>Advertencia del compilador de recursos RC4093
sin secuencias de escape de nueva línea en constante de caracteres en el código inactivo  
  
 La expresión constante de un `#if`, `#elif`, **#ifdef**, o **#ifndef** directiva de preprocesador evaluada como cero, haciendo que el código que sigue inactiva. Dentro del código inactivo, un carácter de nueva línea ha aparecido dentro de un conjunto de comillas simples o dobles.  
  
 Se considera que todo el texto hasta la siguiente marca de comillas doble dentro de una constante de caracteres.