---
title: Advertencia de las herramientas del vinculador LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: fda1fdb03a7629894f846bb20ed84df519239327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183311"
---
# <a name="linker-tools-warning-lnk4102"></a>Advertencia de las herramientas del vinculador LNK4102

exportación del destructor ' name ' de eliminación; es posible que la imagen no se ejecute correctamente

El programa ha intentado exportar un destructor de eliminación. La eliminación resultante puede producirse en un límite de DLL de modo que un proceso pueda liberar memoria de la que no es de su propiedad. Asegúrese de que el símbolo especificado no aparece en el archivo. def y de que el símbolo no aparece como argumento de la opción **/Import** o **/Export** en la línea de comandos del vinculador.

Si va a volver a generar la biblioteca en tiempo de ejecución de C, puede pasar por alto este mensaje.
