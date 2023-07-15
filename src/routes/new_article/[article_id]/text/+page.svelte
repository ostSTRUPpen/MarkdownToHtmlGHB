<script lang="ts">
	let rawText: string = '';
	let htmlText: string = '';
	let html: string = '';
	/*
        text = text.replace("\n", "<br/>")
    while "**" in text:
        text = text.replace("**", "<strong>", 1).replace("**", "</strong>", 1)
    while "*" in text:
        text = text.replace("*", "<i>", 1).replace("*", "</i>", 1)
    */
	$: {
		htmlText = rawText;
		htmlText = htmlText.replaceAll('\n', '<br/>');
		if (htmlText.includes('/')) {
			while (htmlText.includes('/**')) {
				htmlText = htmlText.replace('/**', '<b>').replace('/**', '</b>');
			}
			while (htmlText.includes('/*')) {
				htmlText = htmlText.replace('/*', '<i>').replace('/*', '</i>');
			}
			while (htmlText.includes('/__')) {
				htmlText = htmlText.replace('/__', '<u>').replace('/__', '</u>');
			}
			while (htmlText.includes('/--')) {
				htmlText = htmlText.replace('/--', '<s>').replace('/--', '</s>');
			}
			while (htmlText.includes('/||')) {
				htmlText = htmlText.replace('/||', '<mark>').replace('/||', '</mark>');
			}
            while (htmlText.includes('/hi')) {
				htmlText = htmlText.replace('/hi', '<sup>').replace('/hi', '</sup>');
			}
            while (htmlText.includes('/di')) {
				htmlText = htmlText.replace('/di', '<sub>').replace('/di', '</sub>');
			}
            while (htmlText.includes('/n1')) {
				htmlText = htmlText.replace('/n1', '<h2>').replace('/n1', '</h2>');
			}
            while (htmlText.includes('/n2')) {
				htmlText = htmlText.replace('/n2', '<h3>').replace('/n2', '</h3>');
			}
            while (htmlText.includes('/n3')) {
				htmlText = htmlText.replace('/n3', '<h4>').replace('/n3', '</h4>');
			}
            while (htmlText.includes('/n4')) {
				htmlText = htmlText.replace('/n4', '<h5>').replace('/n4', '</h5>');
			}
		}
	}

	$: {
		html = `<article><div>${htmlText}</div><div></div></article>`;
	}
</script>

<details>
	<summary>Ukázka a návod</summary>
	<div>
		<table>
			<thead>
				<tr>
					<th>Vzhled</th>
					<th>Znakový zápis</th>
					<th>HTML</th>
				</tr>
			</thead>
			<tbody>
				<tr>
					<td><p>Běžný text</p></td>
					<td>Bězný text</td>
					<td> TODO </td>
				</tr>
				<tr>
					<td><p><i>Text kurzívou</i></p></td>
					<td>/*Text kurzívou/*</td>
					<td> TODO </td>
				</tr>
				<tr>
					<td><p><b>Tučný text</b></p></td>
					<td>/**Tučný text/**</td>
					<td> TODO </td>
				</tr>
				<tr>
					<td><p><u>Podtrhnutý text</u></p></td>
					<td>/__Podtrhnutý text/__</td>
					<td> TODO </td>
				</tr>
				<tr>
					<td><p><s>Škrtnutý text</s></p></td>
					<td>/--Škrtnutý text/--</td>
					<td> TODO </td>
				</tr>
				<tr>
					<td><p><mark>Zabarvený text</mark></p></td>
					<td>/||Zabarvený text/||</td>
					<td> TODO </td>
				</tr>
                <tr>
					<td><p>x<sup>Horní index</sup></p></td>
					<td>x/hiHorní index/hi</td>
					<td> TODO </td>
				</tr>
                <tr>
					<td><p>x<sub>Dolní index</sub></p></td>
					<td>x/diDolní index/di</td>
					<td> TODO </td>
				</tr>
                <tr>
					<td><h2>Nadpis článku</h2></td>
					<td>/n1Nadpis článku/n1</td>
					<td> TODO </td>
				</tr>
                <tr>
					<td><h3>Sekundární nadpis</h3></td>
					<td>/n2Sekundární nadpis/n2</td>
					<td> TODO </td>
				</tr>
                <tr>
					<td><h4>Terciární nadpis</h4></td>
					<td>/n3Terciární nadpis/n3</td>
					<td> TODO </td>
				</tr>
                <tr>
					<td><h5>Kvartární nadpis</h5></td>
					<td>/n4Kvartární nadpis/n4</td>
					<td> TODO </td>
				</tr>
			</tbody>
		</table>
	</div>
</details>

<h2>Úprava textu</h2>
<textarea id="article-text" name="article-text" bind:value={rawText} rows="10" cols="100" />

<div id="output">
	{@html html}
</div>

<style>
	#output {
		border: 1px solid black;
	}
</style>
