---
title: Error del compilador de recursos RC2144
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: deabd639e04d5b78b398cda9245e9726e2124740
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642928"
---
# <a name="resource-compiler-error-rc2144"></a>Error del compilador de recursos RC2144

El ID. DE IDIOMA PRINCIPAL no es un número

El ID. DE IDIOMA PRINCIPAL debe ser un identificador en lenguaje hexadecimal. Consulte [Cadenas de idioma y de país o región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) en la *Referencia de la biblioteca en tiempo de ejecución* para obtener una lista de identificadores de idioma válidos.

Este error también puede producirse si los recursos se han agregado y eliminado del archivo .RC utilizando una herramienta. Para corregir este problema, abra el archivo .RC en un editor de texto y limpie manualmente los recursos no utilizados.