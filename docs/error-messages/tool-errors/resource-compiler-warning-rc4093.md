---
title: Advertencia del compilador de recursos RC4093
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 29d24f1e380f5c531e170e5dc23cf5c77eefb874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182297"
---
# <a name="resource-compiler-warning-rc4093"></a>Advertencia del compilador de recursos RC4093

nueva línea sin escape en la constante de caracteres en código inactivo

La expresión constante de una `#if`, `#elif`, **#ifdef**o **#ifndef** Directiva de preprocesador se evalúa como cero, lo que permite que el código siguiente esté inactivo. Dentro de ese código inactivo, aparece un carácter de nueva línea dentro de un conjunto de comillas simples o dobles.

Todo el texto hasta la siguiente comilla doble se consideró dentro de una constante de caracteres.
