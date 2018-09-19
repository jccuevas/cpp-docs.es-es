---
title: Advertencia del compilador de recursos RC4093 | Microsoft Docs
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
ms.openlocfilehash: 9b1ca04b17ebdb9d48bc94032482caf48ad4aa00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111568"
---
# <a name="resource-compiler-warning-rc4093"></a>Advertencia del compilador de recursos RC4093

sin escape de nueva línea en constante de caracteres en el código inactivo

La expresión constante de un `#if`, `#elif`, **#ifdef**, o **#ifndef** directiva de preprocesador evaluada como cero, lo que el código que sigue inactiva. Dentro del código inactivo, un carácter de nueva línea aparece dentro de un conjunto de comillas simples o dobles.

Se considera que todo el texto hasta la siguiente marca de comillas doble dentro de una constante de caracteres.