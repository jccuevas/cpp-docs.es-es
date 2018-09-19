---
title: Error del compilador de recursos RC2144 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2144
dev_langs:
- C++
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f9eb2b25919a2336c36a459ef41eece447a490
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080498"
---
# <a name="resource-compiler-error-rc2144"></a>Error del compilador de recursos RC2144

El ID. DE IDIOMA PRINCIPAL no es un número

El ID. DE IDIOMA PRINCIPAL debe ser un identificador en lenguaje hexadecimal. Consulte [cadenas de idioma y país o región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) en el *referencia de la biblioteca de tiempo de ejecución* para obtener una lista de identificadores de idioma válidos.

Este error también puede producirse si los recursos se han agregado y eliminado del archivo .RC utilizando una herramienta. Para corregir este problema, abra el archivo .RC en un editor de texto y limpie manualmente los recursos no utilizados.