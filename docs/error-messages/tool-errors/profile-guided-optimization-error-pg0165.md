---
title: Error de optimización guiada por perfiles PG0165
description: Describe los errores de PG0165 en los datos de la optimización guiada por perfiles (PGO) de lectura.
ms.date: 10/30/2019
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: c5e5c5d37f8c70a6c2a3d9f7a43c13bb46d0e25a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626803"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Error de optimización guiada por perfiles PG0165

Se produjo un error al leer los datos de optimización guiada por perfiles. Este error puede aparecer en varios formatos:

> Leyendo '*filename. PGD*': ' no se admite la versión de PGD (no coinciden las versiones) '.

Los archivos PGD son específicos de un conjunto de herramientas de compilador determinado. Este error se genera cuando se usa un compilador diferente al utilizado para crear *filename. PGD*. El error indica que este conjunto de herramientas del compilador no puede usar los datos de *filename. PGD* para optimizar el programa actual. Para resolver este problema, vuelva a generar *filename*. PGD con el conjunto de herramientas del compilador actual.

> Leyendo '*nombreDeArchivo. PGD*': ' archivo PGD es de solo lectura '.

Este error se muestra cuando el archivo PGD está marcado como de solo lectura en el sistema de archivos. Para resolver este problema, cambie los atributos de archivo a lectura y escritura.
