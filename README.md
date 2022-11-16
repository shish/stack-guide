Stacked Diffs
=============
<table>
<tr>
	<th width="20%"></th>
	<th width="40%">Pull Request Workflow</th>
	<th width="40%">Stacked Diff Workflow</th>
</tr>
<tr class="images">
	<td></td>
	<td><img src="pr.drawio.svg" /></td>
	<td><img src="stack.drawio.svg" /></td>
</tr>
<tr>
	<td>Unit of code review</td>
	<td>
		<ul>
			<li>Often "all commits merged into one", with individual commits available if you want to see a specific bug get fixed.</li>
			<li>Client and server code reviews are all-or-nothing (unless you split it into two separate pull requests, but then there's no record that the client depends on the server)</li>
			<li>No nice way to review "just the server" or "just the client" (Unless the developer does <code>commit --amend</code> and <code>push --force</code> to create one server commit and one client commit... at which point congratulations, you've invented half-assed stacked diffs :D)</li>
		</ul>
	</td>
	<td>
		<ul>
			<li>Client and server reviewed separately (but linked to show that client depends on server), with the ability to see what changed between eg "Add API (Version 1)" and "Add API (Version 2)" if you want to see a specific bug get fixed.</li>
			<li>The client can be reviewed and approved first, but it can't land until after the server diff lands.</li>
			<li>If for some reason you really want client and server to be reviewed as a single unit, you still have the possibility to submit them as a single diff</li>
		</ul>
	</td>
</tr>
<tr>
	<td>Unit of merge</td>
	<td>
		<ul>
			<li>Client and server are merged into the main branch in one go (unless you cherry-pick individual commits, but this is error-prone)</li>
		</ul>
	</td>
	<td>
		<ul>
			<li>Server and client can be landed together with the "merge stack" button, or the server can be landed first with the "merge diff" button; the client can't be merged until after the server is there.</li>
		<ul>
	</td>
</tr>
<tr>
	<td>Unit of history</td>
	<td>
		<ul>
			<li>5 commits in the history (unless you do an interactive rebase to squash after code review is finished, but then what gets released doesn't match what was reviewed)</li>
		</ul>
	</td>
	<td>
		<ul>
			<li>1 commit for "Add new API to server (v3)" and 1 commit for "Make use of new API in client (v2)"</li>
			<li>Old discarded attemps (eg the buggy "Add new API to server (v1)") aren't in the main branch, but are still visible in the code review tool</li>
		</ul>
	</td>
</tr>
<tr>
	<td></td>
	<td></td>
	<td></td>
</tr>
<tr>
	<td></td>
	<td></td>
	<td></td>
</tr>
<tr>
	<td></td>
	<td></td>
	<td></td>
</tr>
</table>
