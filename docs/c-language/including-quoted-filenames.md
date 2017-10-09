---
title: "Inclusión de nombres de archivo entre comillas | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 17c40e74a31341fc3a725c5e5b3823058e403cff
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="including-quoted-filenames"></a>Inclusión de nombres de archivo entre comillas
**ANSI 3.8.2** Compatibilidad con nombres entrecomillados para archivos de código fuente que se pueden incluir  
  
 Si detalla una especificación de ruta de acceso completa y no ambigua para el archivo de inclusión entre dos elementos de comillas dobles (" "), el preprocesador solo busca la especificación de ruta de acceso y omite los directorios estándar.  
  
 Para los archivos de inclusión especificados como [#include](../preprocessor/hash-include-directive-c-cpp.md) "especificación de ruta de acceso", la búsqueda de directorio comienza con los directorios del archivo primario y continúa con los directorios de los archivos primarios principales. De este modo, la búsqueda comienza en relación con el directorio que contiene el archivo de código fuente que se está procesando actualmente. Si no hay ningún archivo primario principal y no se ha encontrado el archivo, la búsqueda continúa como si el nombre de archivo estuviese entre corchetes angulares.  
  
## <a name="see-also"></a>Vea también  
 [Preprocesar directivas](../c-language/preprocessing-directives.md)
