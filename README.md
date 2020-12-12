# Leistungssteigerung an einem Heizkörper durch erzwungene Konvektion
# Heizung zu schwach, wird nicht warm, was tun?
Wer kennt das nicht? Der Heizkörper ist voll aufgedreht, aber es will einfach nicht richtig warm im Raum werden? Was kann man dagegen tun? Man könnte die sog. Vorlauftemperatur erhöhen. Als Mieter sind einem da aber die Hände gebunden. Bevor man beginnt teuer und umweltschädlich direkt mit Strom zu heizen, sollte man in Betracht ziehen die Leistung eines Heizkörpers mit Ventilatoren zu steigern.

Für diesen Versuch wurde ein Diatherm Flachheizkörper mit 55 cm Höhe und 90 cm Baulänge sowie paralleler Durchströmung beider Platten verwendet. Da ich keine Veränderungen an der Heizungsanlage vornehmen wollte um den Durchfluss zu messen, kann zwar die absolute Heizkörperleistung nicht bestimmt werden, aber die Leistungssteigerung kann mit den gesammelten technischen Daten ermittelt werden.

## Messverfahren um Heizkörperleistungssteigerung zu ermitteln
Es wurden DS18B20 Sensoren von Reichelt, welche laut https://github.com/cpetrich/counterfeit_DS18B20 keine offensichtliche Fälschung sind, mit Wärmeleitpaste und Kabelbinder an Vor- und Rücklauf angebracht, sowie über dem Sensor eine Rohrisolation angebracht um möglichst genau die Vor- und Rücklauftemperaturen erfassen zu können. 

<img src="https://raw.githubusercontent.com/JsBergbau/HeizkoerperLeistungssteigerung/main/Bilder/Sensoren1.jpg" alt="DS18B20 mit Wärmeleitpaste an Heizkörper" title="DS18B20 mit Wärmeleitpaste an Heizkörper" />
<img src="https://raw.githubusercontent.com/JsBergbau/HeizkoerperLeistungssteigerung/main/Bilder/Sensoren2.jpg" alt="DS18B20 mit Rohrisolierung ummantelt" title="DS18B20 mit Rohrisolierung ummantelt" />

Zudem wurde durch ein via Magnet unten angebrachtes Thermometer die Lufteintrittstemperatur gemessen. Da der Sensor etwas im Inneren des Heizkörpers angebracht war, wurden im Vergleich zur Raumtemperatur deutlich erhöhte Messwerte gemessen. Ein weiteres Thermometer befand sich auf direkt oben in der Mitte Heizkörper. Die Werte dieser Thermometer werden für keine Berechnung herangezogen und sind rein informativ.
Das Heizkörperthermostat war für die gesamte Messdauer entfernt, damit der maximale Durchfluss sichergestellt war. Ein voreinstellbares Ventil war durch den Hersteller auf Stufe 3 gestellt. Die Tür zum Flur sowie zu einem anderen unbeheizten Raum war auf um eine möglichst konstante Raumtemperatur für die Messdauer zu haben.

<img src="https://raw.githubusercontent.com/JsBergbau/HeizkoerperLeistungssteigerung/main/Bilder/Thermometer_unten.jpg" alt="Heizkörper Thermometer unten Xiaomi Mi LYWSD03MMC" title="Heizkörper Thermometer unten Xiaomi Mi LYWSD03MMC" />

Als Lüfter wurde der Typ AFB1212SH von Delta Electronics eingesetzt. Diese sind per PWM in der Drehzahl regulierbar. Diese wurden mittels Kabelbindern an den Ecken zu einer langen Reihe verbunden und an 2 Punkten, rechts und links, mit einer Schnur am Heizkörper befestigt.
<img src="https://raw.githubusercontent.com/JsBergbau/HeizkoerperLeistungssteigerung/main/Bilder/Luefterreihe.jpg" alt="7 12 cm Lüfter Delta Electronics AFB1212SH unter Heizkörper" title="7 12 cm Lüfter Delta Electronics AFB1212SH unter Heizkörper" />

Die Leistungsaufnahme wurde mit dem sehr genauen ELV Energy Master gemessen.
## Grafische Auswertung der Heizkörperleistungssteigerung
<img src="https://raw.githubusercontent.com/JsBergbau/HeizkoerperLeistungssteigerung/main/Bilder/Grafische_Auswertung.jpg" alt="Grafana Auswertung Versuch Heizkörperleistungssteigerung" title="Grafana Auswertung Versuch Heizkörperleistungssteigerung" />

### Phase 1: Normaler Betrieb
Unter dem Heizkörper befinden sich keine Lüfter, die Luft kann komplett frei zirkulieren

### Phase 2: Lüfter unter dem Heizkörper
Die Lüfter wurden angebracht und laufen mit PWM auf 50 %. Sie sind nicht unangenehm laut, aber deutlich hörbar. In diesem Zustand beträgt die Leistungsaufnahme des Schaltnetzteils 8,7 W für die 7 Lüfter.

### Phase 3: Lüfter montiert
Die Lüfter sind unter dem Heizkörper aber ausgeschaltet.
### Phase 4: Lüfter kaum hörbar und benötigen 4,9 Watt.
Die Lüfter laufen mit PWM auf 30 %. Auf dieser Stufe sind sie kaum hörbar und benötigen 

Über die gesamte Messdauer hinweg ist schön zu sehen, wie die Raumtemperatur (gelbe Kurve unteres Diagramm) mit Einschalten der Lüfter zu steigen beginnt und bei Abschalten der Lüfter sogar wieder sinkt.

## Detaillierte Auswertung der Leistungssteigerung
Da die Vorlauftemperatur nicht konstant gehalten werden kann, wird für die Ermittlung der Leistungssteigerung auf die Integration der Fläche unter der Kurve aus der Differenz zwischen Vor- und Rücklauftemperatur zurückgegriffen.
Um die Normalleistung zu ermitteln, wird diese Fläche zunächst in Phase 1 ermittelt.
Wie man anhand der Kurve sieht, braucht der Heizkörper ca. 10-15 Minuten bis er einen eingeschwungenen Zustand erreicht. 
Von 16:50 bis 17:50 beträgt dieser Wert 1,174 pro Stunde

<img src="https://raw.githubusercontent.com/JsBergbau/HeizkoerperLeistungssteigerung/main/Bilder/Leistungswert_Phase1.jpg" alt="Heizkörpernormleistungsermittlung" title="Heizkörpernormleistungsermittlung" />

Phase 2 mit Lüftern auf 50 % beginnt um 17:52 und endet um 18:43. Wir werten von 18:10 bis 18:40 aus. Ergibt einen Wert von 1,032. Da dieser Zeitraum nur eine halbe Stunde erfasst, macht das einen Wert von 2,064. Das ergibt somit eine Leistungssteigerung um den Faktor 1,76.

Für Phase 3 ergibt sich ein Wert von 19 Uhr bis 20:30 von 1,14 pro Stunde.

In Phase 4 laufen die Lüfter auf 30 %. Von 21 Uhr bis 22:30 beträgt der Wert 1,65 pro Stunde. Das heißt, obwohl die Lüfter kaum hörbar sind, erzielen sie immer noch eine deutliche Leistungssteigerung. 

## Maximale Lüfterleistung, für maximale Einsparung?

Um zu sehen wieviel Energie sich maximal aus dem Heizkörper holen lässt, wurden die Lüfter über 75 Minuten auf maximaler Leistung betrieben, die letzten 60 Minuten wurde dabei die Leistung gemessen. Die Lüfter waren auf dieser Stufe unangenehm laut und verbrauchten stolze 31,2 Watt. Die Leistung betrug 1,952 Einheiten pro Stunde. Das ist sogar minimal geringer als bei 50 % Leistung. Zunächst klingt das unlogisch, lässt sich aber damit erklären, dass dieser Versuch am nächsten Tag durchgeführt wurde, wo die Vorlauftemperatur zwischen 43 °C und 36 °C schwankte, während beim Versuch mit 50 % die Vorlauftemperatur zwischen 44 °C und 37 °C schwankte. Je kälter der Heizkörper ist, desto geringer kann die Luftdurchströmung ausfallen. 
Wir können also festhalten, ab einem gewissen Punkt, der schnell erreicht ist, ergibt sich kein Vorteil mehr bei der Leistungsabgabe. Ehr im Gegenteil: Die elektrische Leistungsaufnahme sowie der Geräuschpegel steigen überproportional an, während die Leistungsabgabe kaum gesteigert wird.
Der Abstand zwischen den Lamellen ist bei einem Heizkörper relativ groß, da von einer natürlichen Konvektion ausgegangen wird und hierbei die Wärmeübertragung an die Luft deutlich geringer ist. Hier im Wärmebild sieht man deutlich, wie bereits bei 30 % Lüfterleistung die Lamellen in der Mitte deutlich kühler sind. Während sie sie außen, wo sie an der vom Heizwasserdurchströmten Platte anliegen, ca. 46 °C haben, sind es im Inneren nur noch ca. 35 °C und damit 11 K weniger. Deutlich ist zu sehen, wie die Temperatur kontinuierlich von außen nach innen abnimmt.

<img src="https://raw.githubusercontent.com/JsBergbau/HeizkoerperLeistungssteigerung/main/Bilder/ThermobildLuefter30.jpg" alt="Thermografie Heizkörper Lamellen bei 30 % Lüfterleistung" title="Thermografie Heizkörper Lamellen bei 30 % Lüfterleistung" />

Zum Vergleich: Ein Thermobild mit abgeschalteten Lüftern: Hier beträgt der Temperaturunterschied der Lamellen zwischen innen und außen nur ca. 2,5 K. 

<img src="https://raw.githubusercontent.com/JsBergbau/HeizkoerperLeistungssteigerung/main/Bilder/ThermobildOhneLuefter.jpg" alt="Thermografie Heizkörper Lamellen bei natürlicher Konvektion" title="Thermografie Heizkörper Lamellen bei natürlicher Konvektion" />

Möchte man die Leistung des Heizkörpers also besonders effizient steigern, ist es empfehlenswert, wenn die etwas breiter als der Heizkörper sind, sodass sie sowohl vorne als auch hinten die Platten an der Heizkörperaußenseite anblasen können.

## Zusammenfassung der Ergebnisse der Leistungssteigerung

Lüfterstufe | Heizkörperleistung | Leistungsaufnahme | Relative Leistung zur Normleistung
------ |------ | ------ | ------
Ohne | 1,174 | 0 W | 1
30 % | 1,65 | 4,9 W | 141 %
50 % | 2,064 | 8,7 W | 176 %
100 % | 1,952 | 31,2 W | 166 %

## Heizkostensparen durch Lüfter an Heizkörpern? Bei Wärmepumpe ja, sonst fragwürdig
Man liest oft, dass man durch diese Lüfter an den Heizkörpern Heizkosten sparen könne, da man den Vorlauf dadurch geringer einstellen könne. So gibt es unter https://speedcomfort.de/ kommerzielle Lüfter zu kaufen. Jeder Lüfter wird dort mit 0,18 Watt betrieben, Netzteilverluste vermutlich dabei schon enthalten. Zum Vergleich: In der 30 % Einstellung kam in diesem Versuch auf jeden Lüfter eine Leistungsaufnahme von 0,69 Watt. Es handelt sich jedoch um ein sehr günstiges Netzteil mit einem wahrscheinlich relativ geringen Wirkungsgrad bei dieser niedrigen Auslastung.
Die Firma wirbt, dass das Produkt mit 500 Stunden „ausgiebig getestet“ wurde. Der Tag hat 24 Stunden. Also wurde das Produkt gerade einmal 21 Tage und damit weniger als einen Monat getestet. Die 7 Millionen aufgezeichneten Datenpunkte sind ein sehr wenig aussagekräftiger Wert. Würde ich meine ermittelten Daten sekündlich aufzeichnen, käme ich in 21 Tagen auf über 9 Millionen Messpunkte. 

Unabhängig davon, sollte man bedenken, dass durch die verstärkte Luftbewegung im Raum auch mehr Energie durch die Außenwände wieder abgegeben wird. Ob man da bei einer Gastherme wirklich nennenswert Energie sparen kann, bezweifle ich. 
Die Webseite liest sich so, dass ein Teil der Energieeinsparung auch dadurch entsteht, dass man die Temperatur länger abgesenkt lassen kann, weil durch die Lüfter der Raum schneller wieder aufgeheizt wird. Es wurde dort einiges hingerechnet um auf diese hohen Energieeinsparwerte zu kommen. Selbst wenn man Energiesparen kann, wirtschaftlich dürfte das bei einem Preis von aktuell ca. 150 € für 3 Lüftermodule à 3 Lüfter nicht sein. 

Einen wirklich berechtigten Einsatzzweck sehe ich bei einer Wärmepumpe. Hier machen sich reduzierte Vorlauftemperaturen im Energieverbrauch wesentlich stärker bemerkbar. Wenn man den Platz für größere Heizkörper hat, sollte man unbedingt durchrechnen, ob der Austausch gegen größere Heizkörper nicht günstiger ist, als die vorhandenen Heizkörper mit Lüftern auszustatten. Zumal nicht jeder Heizkörper einen Stromanschluss in der Nähe hat und man dann im schlimmsten Fall ein Kabel quer durch den Raum liegen hat. 

## Heizkostensparen bei Heizkostenverteilern
Was die Webseite verschweigt: Hat man Heizkostenverteiler an den Heizkörpern, wie man diese häufig in Mietswohnungen findet, führt das zu einer erheblichen Mindermessung des Messgerätes und damit zu einer vermeintlichen Energieeinsparung. 
Durch die Leistungssteigerung können die verbrauchsabhängigen Heizkosten ca. halbiert werden, denn zu der gesteigerten Leistungsabgabe des Heizkörpers kommt auch noch eine geringere Oberflächentemperatur hinzu. Hier ist eine enorme Einsparung möglich. Allerdings nutzt man dadurch das Messprinzip stark zu seinen Gunsten aus, weil dieses nur die Temperatur des Heizkörpers misst und darauf der errechnete Verbrauch basiert. Im Gegenzug werden die Nachbarn eine höhere Heizkostenrechnung bekommen, da Heizkostenverteiler die Heizkosten auf alle Parteien verteilen. 
Andererseits ist misst so ein Heizkostenverteiler sehr unzuverlässig und schnell hat man dadurch unnötig hohe Heizkosten, da man mit Vorhängen, Möbeln, Gegenstände auf der Heizung die Wärmeabgabe des Heizkörpers verringert bei gleichzeitiger Temperaturerhöhung des Heizkörpers. So werden die Heizkosten unnötig in die Höhe getrieben, während man sogar weniger Energie bezieht. Wer mehr dazu wissen möchte, dem sei das Dokument <a href="https://de.scribd.com/document/111375633/Heizkosten">Heizkostensparen in Mietshäusern oder über die Ungerechtigkeit der Heizkostenverteiler</a> nahgelegt. 

## Rohdaten
Die Rohdaten der Messreihe finden sich im CSV-Format in diesem Repository.

## Lizenz 
Dieses Dokument inklusive der Rohdaten und Ressourcen wird unter der CC BY NC SA Lizenz veröffentlicht https://creativecommons.org/licenses/by-nc-sa/4.0/deed.de. Kommerzielle Nutzung kann auf Anfrage, je nach geplantem Verwendungszweck sogar kostenlos, gestattet werden.
