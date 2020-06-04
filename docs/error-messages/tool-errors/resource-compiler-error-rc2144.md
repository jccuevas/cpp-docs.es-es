---
title: Error del compilador de recursos RC2144
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: 1b080916642fc1be4b22820668c4cb4137675425
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191202"
---
# <a name="resource-compiler-error-rc2144"></a>Error del compilador de recursos RC2144

El ID. DE IDIOMA PRINCIPAL no es un número

El ID. DE IDIOMA PRINCIPAL debe ser un identificador en lenguaje hexadecimal. Consulte [Cadenas de idioma y de país o región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) en la *Referencia de la biblioteca en tiempo de ejecución* para obtener una lista de identificadores de idioma válidos.

Este error también puede producirse si los recursos se han agregado y eliminado del archivo .RC utilizando una herramienta. Para corregir este problema, abra el archivo .RC en un editor de texto y limpie manualmente los recursos no utilizados.
