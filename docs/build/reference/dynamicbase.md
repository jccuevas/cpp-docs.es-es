---
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: ab7682c8344d6fc36ded03e7ef885c83d2f19ab7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169050"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Especifica si se genera una imagen ejecutable que se puede reorganizar aleatoriamente en el momento de la carga mediante la característica de selección aleatoria del diseño del espacio de direcciones (ASLR) de Windows que primero estaba disponible en Windows Vista.

## <a name="syntax"></a>Sintaxis

> **/dynamicbase**[ **: no**]

## <a name="remarks"></a>Observaciones

La opción **/dynamicbase** modifica el encabezado de una *imagen ejecutable*, un archivo. dll o. exe, para indicar si la aplicación se debe reorganizar aleatoriamente en el momento de la carga y permite la selección aleatoria de asignación de direcciones virtuales, que afecta a la ubicación de la memoria virtual de montones, pilas y otras asignaciones del sistema operativo. La opción **/dynamicbase** se aplica a las imágenes de 32 bits y de 64 bits. ASLR es compatible con Windows Vista y sistemas operativos posteriores. Los sistemas operativos anteriores omiten la opción.

De forma predeterminada, **/dynamicbase** está habilitado. Para deshabilitar esta opción, use **/dynamicbase: no**. La opción **/dynamicbase** es necesaria para que la opción [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) tenga un efecto.

## <a name="see-also"></a>Consulte también

- [Opciones de EDITBIN](editbin-options.md)
- [Defensas de seguridad de software de ISV de Windows](https://msdn.microsoft.com/library/bb430720.aspx)
