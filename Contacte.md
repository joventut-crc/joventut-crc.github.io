---
layout: post
title:  "Contacte"
---

<center>

<script>var map;
var arrowPolyline = L.Polyline.extend({
        addArrows: function(){
		    var points = this.getLatLngs()
            for (var p = 0; p +1 < points.length; p++){
                
                var diffLat = points[p+1]["lat"] - points[p]["lat"]
                var diffLng = points[p+1]["lng"] - points[p]["lng"]
                var center = [points[p]["lat"] + diffLat/2,points[p]["lng"] + diffLng/2]
               
                var angle = 360 - (Math.atan2(diffLat, diffLng)*57.295779513082)
                
                var arrowM = new L.marker(center,{
                   icon: new L.divIcon({ 
                        className : "arrowIcon",
                        iconSize: new L.Point(30,30), 
                        iconAnchor: new L.Point(15,15), 
                        html : "<div style = 'font-size: 20px; -webkit-transform: rotate("+ angle +"deg)'>&#10152;</div>"
                   })
                }).addTo(map);
           }
            
        }
    })

$( document ).ready(function() {
	map = L.map('map').setView([41.40533, 2.16773], 18);
    
	L.tileLayer('http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
		maxZoom: 18,
		opacity: 0.6
	}).addTo(map);
    
   var latlngs = [[41.40565, 2.16700], [41.40547, 2.16722], [41.40537, 2.16703], [41.40529, 2.16713]]    
   var polyline = new arrowPolyline(latlngs, {color: '#708238'}).addTo(map);
   polyline.addArrows()
    
    L.marker([41.40530, 2.16716], {icon: L.icon({iconUrl: '{{ site.baseurl }}/assets/img/crc.png',iconSize:[36]})}).addTo(map);
})
</script>
<style>
#map {
    height: 500px;
    width: 80%;
}
</style>

<div id = "map"></div>
  <h3>Dirección: c. Nàpols, 338 local 4  08025 Barcelona</h3>
  <h3><a href="mailto:joventutcerecusor3@gmail.com" target="_top">joventutcerecusor3@gmail.com</a></h3>
</center>
