---
title: Advertencia del compilador de recursos RC4093
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 23bf436e6e8338f89bc576564181c84715028332
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346215"
---
# <a name="resource-compiler-warning-rc4093"></a>Advertencia del compilador de recursos RC4093

sin escape de nueva línea en constante de caracteres en el código inactivo

La expresión constante de un `#if`, `#elif`, **#ifdef**, o **#ifndef** directiva de preprocesador evaluada como cero, lo que el código que sigue inactiva. Dentro del código inactivo, un carácter de nueva línea aparece dentro de un conjunto de comillas simples o dobles.

Se considera que todo el texto hasta la siguiente marca de comillas doble dentro de una constante de caracteres.