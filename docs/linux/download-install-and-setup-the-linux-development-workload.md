---
title: Descargar, instalar y configurar la carga de trabajo de Linux | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e11b40b2-f3a4-4f06-b788-73334d58dfd9
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: dff1e9e03911f65dfcffcd078e0739224f73f4aa
ms.openlocfilehash: 09ce0024b7a98729b28968fff081ed105b5463e1
ms.lasthandoff: 02/24/2017

---

# <a name="download-install-and-setup-the-linux-workload"></a>Descargar, instalar y configurar la carga de trabajo de Linux

## <a name="visual-studio-setup"></a>Instalación de Visual Studio
1. Inicie el instalador de Visual Studio y seleccione la carga de trabajo **Desarrollo de Linux con C++**.

   ![Extensión Visual C++ para desarrollo de aplicaciones para Linux](media/linuxworkload.png)

2. Haga clic en **Instalar** para continuar con la instalación.

## <a name="linux-setup"></a>Instalación de Linux
El equipo Linux de destino debe tener **openssh-server**, **g++**, **gdb** y **gdbserver** instalados y ssh daemon debe estar en ejecución.  Si aún no están instalados, puede instalarlos como sigue:
 
1. En un símbolo del sistema del shell del equipo Linux, ejecute:

   `sudo apt-get install openssh-server g++ gdb gdbserver`

   Debido al comando sudo, es posible que se le pida la contraseña raíz.  Si es así, escríbala y continúe.  Una vez que haya finalizado, se instalarán estos servicios y herramientas.

1. Asegúrese de que el servicio ssh se esté ejecutando en el equipo Linux al ejecutar:

   `sudo service ssh start`
   
   Esto iniciará el servicio y lo ejecutará en segundo plano, listo para aceptar conexiones.

