---
title: Error del compilador de recursos RC2144 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2144
dev_langs: C++
helpviewer_keywords: RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c29a1c1f392372b8dfddd84fa9693010e6a52bfa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2144"></a>Error del compilador de recursos RC2144
El ID. DE IDIOMA PRINCIPAL no es un número  
  
 El ID. DE IDIOMA PRINCIPAL debe ser un identificador en lenguaje hexadecimal. Vea [cadenas de idioma y país o región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) en el *referencia de la biblioteca de tiempo de ejecución* para obtener una lista de identificadores de idioma válidos.  
  
 Este error también puede producirse si los recursos se han agregado y eliminado del archivo .RC utilizando una herramienta. Para corregir este problema, abra el archivo .RC en un editor de texto y limpie manualmente los recursos no utilizados.