[Le pdf à télécharger](accords.pdf) - Adresse réduite de cette page :
[huit.re/acc-uke](https://huit.re/acc-uke)

Ce document est une présentation de quelques accords du ukulele accordé comme
les quatre cordes aigues de la guitare.

Il comporte deux tableaux :

* un où les accords sont organisés par fondamentale et couleur,
* un autre où ils sont organisés par tonalité et degrés.

Attention, ce n’est pas un cours de ukulele, plutôt un support pour un cours.

## Dernières modifications du pdf

<div id="liste"></div>

## Compilation

Pour produire le pdf vous-même, vous aurez besoin d’une chaîne de compilation
LaTeX standard et du paquet [songs](http://songs.sourceforge.net/).

## Remarques et suggestions

Envoyer un email à <profgra.org@gmail.com> ou
[créer un ticket](https://github.com/Grahack/accords_ukulele/issues/new)
dans le [QG de développement de ce doc](https://github.com/Grahack/accords_ukulele/).

<div id="zarbi">Le code zarbi ci-dessous, c’est pour la liste des mises
à jour du pdf sur la github page.</div>

<script type="text/javascript" src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
<style type="text/css">
    ul.liste {list-style: none;}
    ul.liste li {padding-bottom: 5px;}
</style>
<script type="text/javascript">
    $('#zarbi').html('');
    var target_elt = $('#liste');
    var endpoint = "https://api.github.com/repos/Grahack/accords_ukulele/";
	var url = endpoint + "commits?path=accords.pdf";
    var request = $.get(url, {}, function() {}, 'jsonp');
    request.done(function(data) {
        var ul = $('<ul/>').addClass('liste').appendTo(target_elt);
        $.each(data.data, function(i, item) {
            var li = $('<li/>').appendTo(ul);
            var b = $('<b/>').appendTo(li);
            var date = item.commit.author.date;
            var cleanedDate = date.replace('T',' ').replace('Z',' ');
            b.append(cleanedDate);
            var msg = item.commit.message;
            if (msg.slice(0, 5) === "PDF: ") {
                msg = msg.slice(5);
            }
            li.append(b);
            li.append(" - " + msg);
            if ( i === 4 ) {  // max items
                return false;
            }
        });
    });
</script>
