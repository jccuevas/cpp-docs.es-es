---
title: Actualizar C++ proyectos desde versiones anteriores de Visual Studio
description: Cómo actualizar proyectos de Microsoft C++ desde versiones anteriores de Visual Studio.
ms.date: 10/29/2019
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
ms.openlocfilehash: b317271a9cd0873e60a6dd9acd1b73a766aaea19
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627168"
---
# <a name="upgrade-c-projects-from-earlier-versions-of-visual-studio"></a>Actualizar C++ proyectos desde versiones anteriores de Visual Studio

Para actualizar un proyecto creado en Visual Studio 2008 o versiones anteriores, primero debe usar Visual Studio 2010 para convertir el proyecto del formato VCBuild (. vcproj) al formato MSBuild (. vcxproj). Para obtener más información, vea las [instrucciones para Visual Studio 2008](use-native-multi-targeting.md#instructions-for-visual-studio-2008).

Para actualizar un proyecto creado en Visual Studio 2010 o posterior, simplemente abra el proyecto en la versión más reciente de Visual Studio. Visual Studio ofrece la actualización del proyecto al esquema actual. Si elige **no**y tiene la versión anterior de Visual Studio en el equipo, puede trabajar en el proyecto en una versión más reciente de Visual Studio y seguir teniendo como destino el conjunto de herramientas anterior. Por ejemplo, si el proyecto debe seguir ejecutándose en Windows XP, puede actualizarlo a Visual Studio 2019, pero debe especificar el conjunto de herramientas como v141 o anterior. Para obtener más información, vea [Use native multi-targeting in Visual Studio to build old projects](use-native-multi-targeting.md) (Usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos). Si elige **sí**, el proyecto se convertirá y no se podrá volver a convertir a la versión anterior. Por lo tanto, en escenarios de actualización, es recomendable realizar una copia de los archivos de proyecto y de solución existentes.

## <a name="upgrade-reports"></a>Actualizar informes

Al actualizar un proyecto, obtendrá un informe de actualización, que también se guarda en la carpeta del proyecto como UpgradeLog.htm. El informe de actualización muestra un resumen de los problemas que se han producido y alguna información acerca de los cambios que se realizaron, incluido:

1. Propiedades del proyecto

2. Archivos de inclusión

3. Código que ya no se compila correctamente debido a las mejoras de conformidad del compilador o a los cambios en el estándar

4. Código que se basa en características de Windows o Visual Studio que ya no están disponibles o archivos de encabezado que no se incluyen en una instalación predeterminada de Visual Studio o que se han quitado del producto.

5. Código que ya no se compila debido a cambios en las API, como las API cuyo nombre se ha cambiado, firmas de función cambiadas o funciones en desuso.

6. Código que ya no se compila debido a cambios en los diagnósticos, como una advertencia que se convierte en un error.

7. Errores del vinculador debidos a bibliotecas que se cambiaron, especialmente cuando se utiliza /NODEFAULTLIB.

8. Errores en tiempo de ejecución o resultados inesperados debidos a cambios de comportamiento.

9. Errores que se introdujeron en las herramientas. Si encuentra un problema, informe al equipo de Visual C++ a través de los canales de soporte normales o mediante la página de la [comunidad de desarrolladores de Visual Studio C++](https://developercommunity.visualstudio.com/spaces/62/index.html).

Algunos proyectos y soluciones actualizados se pueden compilar correctamente sin modificarlos. Sin embargo, la mayoría de los proyectos probablemente requerirán cambios en la configuración del proyecto, así como en el código fuente. No existe una única manera correcta de solucionarlos, pero se recomienda algún tipo de enfoque por fases. Antes de comenzar, revise la [información general de los posibles problemas de actualización](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) para obtener más información sobre muchos tipos de errores comunes.

 1. Establezca el conjunto de herramientas C++ de la plataforma, el estándar del lenguaje y la versión Windows SDK (si procede) en las versiones deseadas. ( **Propiedades del** **proyecto** >  > **propiedades de configuración** > **General**)
 1. Si tiene muchos errores, desactive la opción [permissive](../build/reference/permissive-standards-conformance.md) ( **propiedades** de**Project** >  > **propiedades de configuración** > **lenguaje** **CC++ /**  > ) y análisis de [código ](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)(Las **propiedades** del**proyecto** >  > **propiedades de configuración** > el análisis de **código**) para reducir el recuento de errores de forma temporal.
 1. Asegúrese de que todas las dependencias están presentes y de que las rutas de acceso de inclusión o las ubicaciones de biblioteca son correctas. (Propiedades del**proyecto** ** >  > ** **propiedades de configuración** > directorios de **VC + +** )
 1. Identifique y corrija los errores debidos a las referencias a las API que ya no existen.
 1. Corrija los errores restantes que impidan la compilación. Consulte [información general sobre posibles problemas de actualización](../porting/overview-of-potential-upgrade-issues-visual-cpp.md) para las correcciones de errores comunes.
 1. Vuelva **a** activar las recuperaciones y corrija los errores nuevos que aparecen debido a código no compatible que se compiló previamente en MSVC.
 1. Active el análisis de código para identificar los posibles problemas o los patrones de codificación obsoletos que ya no se consideran aceptables. Si el análisis de código marca muchos errores, puede desactivar algunas de las advertencias para centrarse primero en las más importantes. El IDE puede ayudar con correcciones rápidas para algunos tipos de problemas.
 1. Considere otras oportunidades para modernizar el código, por ejemplo, reemplazando las estructuras de datos y los algoritmos personalizados C++ por los de la biblioteca estándar o la biblioteca de código abierto de Boost. Mediante el uso de características estándar, facilita a los demás el mantenimiento del código y también tiene una confianza segura de que el código ha sido probado y revisado por muchos expertos en el Comité de estándares y la C++ comunidad más amplia.

En caso de errores difíciles de corregir, intente buscar o publicar una pregunta en Stack Overflow o [ C++ ](https://developercommunity.visualstudio.com/spaces/62/index.html)en la comunidad de desarrolladores.

## <a name="in-this-section"></a>En esta sección

[Información general sobre posibles problemas de actualización](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Actualizar código a CRT universal](upgrade-your-code-to-the-universal-crt.md)<br/>
[Actualizar WINVER y _WIN32_WINNT](modifying-winver-and-win32-winnt.md)<br/>
[Corregir dependencias en los datos internos de biblioteca](fix-your-dependencies-on-library-internals.md)<br/>
[Problemas de migración de punto flotante](floating-point-migration-issues.md)<br/>
[C++características desusadas en Visual Studio 2019](features-deprecated-in-visual-studio.md)<br/>
[VCBuild frente a MSBuild](build-system-changes.md)<br/>
[Puerto de bibliotecas de terceros](porting-third-party-libraries.md)<br/>

## <a name="see-also"></a>Vea también

[Novedades de Visual C++ en Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Historial de cambios en Visual C++ 2003-2015](../porting/visual-cpp-change-history-2003-2015.md)<br/>
[Comportamiento no estándar](../cpp/nonstandard-behavior.md)<br/>
[Aplicaciones de datos de Puerto](../data/data-access-programming-mfc-atl.md)<br/>
