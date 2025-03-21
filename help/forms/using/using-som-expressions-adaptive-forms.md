---
title: Verwenden von SOM-Ausdrücken in adaptiven Formularen
description: Erfahren Sie, wie Sie SOM-Ausdrücke eines Bedienfelds in einem adaptiven Formular extrahieren.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
feature: Adaptive Forms,Foundation Components
discoiquuid: 13f00bb2-561f-4d64-8829-292c663abeab
docset: aem65
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: a2a2a6f3-409e-44a2-a85b-9f0bc40cc800
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 100%

---

# Verwenden von SOM-Ausdrücken in adaptiven Formularen{#using-som-expressions-in-adaptive-forms}

Adaptive Formulare werden als AEM-Seite modelliert, die im AEM-Repository als JCR-Inhaltstruktur dargestellt wird. Das Schlüsselelement der Inhaltsstruktur ist der Knoten „guideContainer“. Unter „guideContainer“ befindet sich der Knoten „rootPanel“, der verschachtelte Bedienfelder und Felder enthalten kann.

Sie können ein Skripting-Objektmodell (SOM) verwenden, um Werte, Eigenschaften und Methoden innerhalb eines bestimmten Dokumentobjektmodells (DOM) zu referenzieren. Ein DOM organisiert die Speicherobjekte und Eigenschaften in einer hierarchischen Baumstruktur. Ein SOM-Ausdruck verweist auf Felder/Zeichenelemente und Bedienfelder.

Die folgende Abbildung zeigt eine Knotenstruktur, in die ein adaptives Formular umgesetzt wird, wenn Sie einem Formular Komponenten hinzufügen. Sie können beispielsweise dem Stammbereich einen Bereich und diesem dann ein Optionsfeld hinzufügen. Der Bereich wird dann zur Laufzeit in ein DOM transformiert. Der SOM-Ausdruck für das Optionsfeld im adaptiven Formular wird als `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]` angegeben.

![DOM-Baumstruktur](assets/hierarchy.png)

DOM-Baumstruktur

Einem SOM-Ausdruck für ein beliebiges Element in einem adaptiven Formular wird das Präfix `guide[0].guide1[0]` vorangestellt. Die Position einer Komponente in der hierarchischen Knotenstruktur wird zum Ableiten des entsprechenden SOM-Ausdrucks verwendet.

![DOM-Baumstruktur mit zwei Optionsfeldern](assets/hierarchy_radio_button.png)

DOM-Baumstruktur mit zwei Optionsfeldern

Der SOM-Ausdruck ändert sich, wenn Sie die Position der Optionsfelder im adaptiven Formular ändern. Im Authoring-Modus können Sie den SOM-Ausdruck eines Felds oder Elements in AEM Forms mithilfe der Option „SOM-Ausdruck anzeigen“ anzeigen. Die Option wird auf dem Bereich angezeigt und wenn Sie mit der rechten Maustaste auf das Feld oder Element klicken.

![Extrahieren von SOM-Ausdrücken in einem adaptiven Formular](assets/som-expressions.png)

Extrahieren von SOM-Ausdrücken in einem adaptiven Formular

Innerhalb von Bereichen können Sie von der Bereichssymbolleiste aus auf die Funktion zugreifen. Die Funktion vereinfacht die Skripterstellung durch Autoren adaptiver Formulare.

![Extrahieren von SOM-Ausdrücken mithilfe der Bereichssymbolleiste](assets/som-expression.png)

Extrahieren von SOM-Ausdrücken mithilfe der Bereichssymbolleiste

Einige in [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html) aufgeführte APIs verwenden den SOM-Ausdruck eines Elements. Um beispielsweise ein bestimmtes Feld in einem adaptiven Formular hervorzuheben, muss der entsprechende SOM-Ausdruck an die `getFocus`-API in `guideBridge` übergeben werden.
