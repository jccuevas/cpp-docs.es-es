---
title: Advertencia del compilador de recursos RC4093 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4093
dev_langs:
- C++
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cca3c2a139e1109746f3a690cfb3f31509a9fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-warning-rc4093"></a>Advertencia del compilador de recursos RC4093
sin secuencias de escape de nueva línea en constante de caracteres en el código inactivo  
  
 La expresión constante de un `#if`, `#elif`, **#ifdef**, o **#ifndef** directiva de preprocesador evaluada como cero, haciendo que el código que sigue inactiva. Dentro del código inactivo, un carácter de nueva línea ha aparecido dentro de un conjunto de comillas simples o dobles.  
  
 Se considera que todo el texto hasta la siguiente marca de comillas doble dentro de una constante de caracteres.