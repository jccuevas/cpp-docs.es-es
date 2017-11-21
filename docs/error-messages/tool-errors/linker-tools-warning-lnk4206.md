---
title: Las herramientas del vinculador LNK4206 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4206
dev_langs: C++
helpviewer_keywords: LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1227cd792065198a3cd7f7a684e51e7c87452e77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4206"></a>Advertencia de las herramientas del vinculador LNK4206
información de tipo precompilado no se encuentra; 'filename' no vinculado o reemplazado; se vinculará el objeto sin información de depuración  
  
 El archivo objeto dado, compilado con [/Yc](../../build/reference/yc-create-precompiled-header-file.md), no se especificó en el comando LINK o se sobrescribió.  
  
 Un escenario común para esta advertencia es cuando el archivo .obj que se compiló con/Yc está en una biblioteca, y donde no hay ningún símbolo hace referencia a dicho archivo .obj desde el código.  En ese caso, el vinculador no use (ni incluso ver) del archivo .obj.  En esta situación, debe volver a compilar el código y usar [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) para los objetos restantes (los objetos que no están compilados con/Yc).