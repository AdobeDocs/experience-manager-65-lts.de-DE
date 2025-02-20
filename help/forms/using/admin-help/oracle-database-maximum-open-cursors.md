---
title: Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank
description: Erfahren Sie mehr über die Konfiguration eines Maximalwerts für geöffnete Cursors in Oracle.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 100%

---

# Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank {#oracle-database-maximum-open-cursors-threshold}

Um einen Maximalwert für geöffnete Cursors in Oracle zu konfigurieren, müssen Sie diesen Wert möglicherweise auf eine Zahl einstellen, die für Ihre Anwendung geeignet ist.  Es ist offensichtlich, dass die durchschnittliche Anzahl geöffneter Cursors bei mittlerer Auslastung 2700 betrug.  Es wird empfohlen, mit einem oberen Grenzwert von 3000 zu beginnen.  Weitere Informationen finden Sie unter [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
